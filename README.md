# AI-UNH-FAQ-BOT

University of New Haven FAQ Chatbot
Documentation
Overview
This document provides a comprehensive guide for setting up and using the
FAQ Chatbot designed for the University of New Haven. The bot leverages a
large language model, LangChain, and a vector database (Pinecone) to
deliver accurate answers to students' inquiries.
Code Link: (https://github.com/MSDS-Virtual-Advisor-Project/MSDS-Chatbot/)

Project Structure
The project consists of two main Python files:
• `main flask app.py`: The Flask server and web application responsible
for handling user queries and displaying the chat interface.
• `loaddata.py`: A script responsible for scraping, processing, and
loading the necessary data into the vector database.
• Static and templates for UI of the chatbot
Prerequisites
• - Python 3.8 or higher
• - Flask
• - MongoDB account and cluster
• - Pinecone account
• - OpenAI API key
• - `.env` file with necessary environment variables
Setup
1. Environment Variables
Ensure you have a `.env` file with the following variables:
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=your_pinecone_environment
PINECONE_INDEX=your_pinecone_index_name 
2. MongoDB Configuration
Create a MongoDB database and collection where conversations will be
stored. Update the `client` in `main flask app.py` with your MongoDB URI.
3. Pinecone Configuration
Set up a Pinecone account and create an index. Update the
`PINECONE_API_KEY`, `PINECONE_ENVIRONMENT`, and `PINECONE_INDEX`
in your `.env` file with the appropriate values.
4. Install Dependencies
Install all the required Python packages using:
pip install –r requirements.txt
Running the Application
Data Loading
(Optional step as the data is already loaded)
a. Execute `loaddata.py`
Before running the chatbot, execute `loaddata.py` to scrape, process, and
load the FAQs into Pinecone. It will perform the following actions:
- Scrape the specified URLs from the sitemap.
- Download PDF files and extract the content.
- Split the content into manageable chunks.
- Load these chunks into Pinecone vector database.
Starting the Flask App
a. Run `python app.py`
Execute the Flask application by running `python app.py`. This will start the
web server.
• You can also run the app using docker
• docker build -t unh-faq-bot . to build an image
docker run -p 5000:5000 unh-faq-bot to run container
b. Accessing the Web Interface
Open a web browser and navigate to `http://localhost:5000/` to interact
with the chatbot.
Usage
Interacting with the Chatbot
- Users can type their questions into the chat interface.
- The chatbot will process the question and return an answer along with
sources, if available.
Managing the Data
• All conversations will be stored in the MongoDB collection specified in
`main flask app.py`.
• Use MongoDB's tools to manage and analyze the stored conversation
data.
Troubleshooting
If any issues arise during setup or while using the chatbot, check the
following:
- Environment variables are correctly set in the `.env` file.
- MongoDB URI is correctly set and the database is accessible.
- Pinecone index is properly configured and has the correct permissions.
- API keys for Pinecone and OpenAI are valid and have not exceeded their
limits.
Conclusion
This documentation outlines the process for setting up and running the
University of New Haven FAQ Chatbot. Follow each step carefully to ensure
a smooth operation of the chatbot. For further assistance or to report any
issues, please contact the development team.
