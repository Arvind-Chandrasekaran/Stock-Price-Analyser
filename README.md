# Stock-Price-Analyser

#### Stock Price Prediction with News Sentiment Analysis
##### This project is a full-stack, microservices-based application designed to predict stock prices by leveraging historical stock data and financial news sentiment. The entire pipeline, from data collection to prediction, is containerized and deployed on AWS Elastic Container Service (ECS) for scalability and reliability.

#### Project Description
##### This application utilizes a microservice architecture to create a robust and scalable system for stock price prediction. The architecture is composed of four distinct services, each with a specific responsibility: data collection, data retrieval, analytics, and authentication.
##### The workflow begins with the Collection Service fetching historical stock data via the yfinance library, which is then stored in a durable AWS S3 bucket. When a specific time range of data is required for analysis, the Retrieval Service efficiently queries and moves the relevant data from S3 to a DynamoDB table.
###### The core predictive power resides within the Analytics Service. This service employs Facebook Prophet, a powerful time-series forecasting tool, to model and predict future stock prices based on historical trends. To improve prediction accuracy, it incorporates sentiment analysis of financial news headlines using the VADER (Valence Aware Dictionary and sEntiment Reasoner) model. This allows the model to factor in market sentiment. The Authentication Service secures the application, managing access and ensuring that only authorized users or services can interact with the system.
##### The entire application is deployed on AWS Elastic Container Service (ECS), which orchestrates the Docker containers for each microservice, ensuring high availability and seamless scaling.

#### Architecture: Microservices
##### The application is built using a microservice architecture, which allows for independent development, deployment, and scaling of each component. The system is composed of the following four microservices:

#### Authentication Service
##### This service is responsible for securing the application by managing user and service authentication. It ensures that all interactions within the system are authorized, providing a secure gateway to the application's features and data.

#### Collection Service
##### This service handles the automated ingestion of data. It periodically fetches historical stock data from Yahoo Finance using the yfinance library and stores it in an AWS S3 bucket for long-term, scalable storage.
##### Sentiment Analysis: It analyzes financial news headlines using the VADER model to generate sentiment scores, capturing the market's mood.

#### Retrieval Service
##### The Retrieval Service is responsible for fetching specific subsets of data from storage. When the analytics pipeline needs to be run, this service queries the S3 bucket for a specified time range and efficiently loads the data into a DynamoDB table, which is optimized for the fast, time-series queries required for analysis.

#### Analytics Service
##### This is the core analytical engine of the project. It retrieves the time-series data from DynamoDB and performs : 
##### Time-Series Forecasting: It utilizes Facebook Prophet to build a predictive model. The historical stock data is used for training, and the sentiment scores are incorporated as an additional regressor to enhance the model's predictive accuracy.

#### Technologies Used
##### Microservices Framework: Your chosen framework (e.g., Flask, FastAPI, Spring Boot)
##### Data Collection: Python, yfinance
##### Cloud Storage & Database: AWS S3, AWS DynamoDB
##### Data Analysis & Forecasting: Pandas, NumPy, Facebook Prophet
##### Sentiment Analysis: NLTK, VADER
##### Deployment/Infrastructure: Docker, AWS Elastic Container Service (ECS)
##### Authentication: Your chosen authentication library/framework (e.g., JWT, OAuth)

#### Workflow
##### Data Ingestion: The Collection Service fetches historical stock data and stores it in an AWS S3 bucket.
##### Data Retrieval: The Retrieval Service queries S3 for data within a specific time range and loads it into a DynamoDB table.
##### Analysis & Prediction: The Analytics Service retrieves data from DynamoDB, performs sentiment analysis on news headlines, and uses this along with the historical data to train a Prophet model and generate price predictions.
##### Secure Access: The Authentication Service manages access control for all incoming requests to the various services.
##### Deployment: All microservices are containerized with Docker and deployed on AWS ECS, which handles the lifecycle, scaling, and networking of the containers.

#### Analytics Microservice - https://github.com/Arvind-Chandrasekaran/SENG3011_OMEGA_Analytics
#### Collection and Retrieval Microservice - https://github.com/AIS170/SENG3011_OMEGA
#### Front End - https://github.com/AIS170/SENG3011_OMEGA_frontend
#### Authentication Microservice - https://github.com/AIS170/SENG3011_OMEGA_Authentication
