# Campus_Ready

## Setup Instructions

### 1. Install Dependencies

Before running the script, ensure all required dependencies are installed. To do this, run the following command to install the necessary packages from the `requirements.txt` file:

pip install -r requirements.txt

### 2. Create a postgres database
Create a PostgreSQL database to store structured data, such as complex tables with merged cells, ensuring proper handling of such data from any PDF.

Note that this will be managed using the SQL_Agent file, which will interact with and process the data. Keep this in mind for later steps.

If you're working with a very simple PDF that doesn't contain complex tables or feel this step is unnecessary, you can comment out this part in File_service file.

### 3. Create the .env File
replace data in .env file with your own credentials

### 4. Uploading a Book to Chroma
To upload any book to Chroma, follow these steps:

Ensure the File_Service file is correctly set up and the necessary dependencies are installed.

In the File_Service file, 

Provide the file_path of the PDF file you want to upload. This path should point to the location of the PDF on your system.

uncomment the following two lines to upload a PDF file:
chatbot = AiCompanyFileService()
response = asyncio.run(chatbot.document_uploading(file_path))
print(response)

Run the script, and the book will be processed, its content split into chunks, and embeddings will be stored in Chroma.



### 5. Deleting Files from Chroma and PostgreSQL
uncomment the following two lines to delete a PDF file:
response = chatbot.delete_pdf_for_company(file_path)
print(response)

Run the script, and the specified file will be deleted from both Chroma and the PostgreSQL database



### 6. Running the Main Agent with Tools for Extracting Topics and Generating Questions
To extract the main topics and generate questions from a PDF, follow these steps:

Ensure the necessary files are set up and dependencies are installed.

Run the Tools file to activate the main agent, which will handle the topic extraction and question generation

The main agent will process the PDF, extract key topics, and generate relevant questions based on the content of the book.


## Tools and Frameworks Chosen

- **LangChain**: A framework for building applications with large language models (LLMs). It provides tools for text splitting, document processing, and interacting with vector stores like Chroma.
  
- **OpenAI**: Used for generating embeddings of text data via GPT models. The OpenAI API helps create semantically meaningful representations of text.

- **Azure Document Intelligence**: A suite of AI-powered tools from Microsoft Azure to extract structured data (e.g., tables, text) from PDFs, including complex documents with merged cells.

- **Chroma**: A vector store used to persist document embeddings and perform fast similarity search. It stores the chunks of text generated from PDFs and the corresponding embeddings.

- **PyMuPDF (fitz)**: A Python library for reading, extracting, and processing PDF files. It's used to load PDFs, extract text, and split it into chunks.

- **SQLAlchemy / psycopg2**: A library to interact with PostgreSQL databases. It’s used to store and manage structured data, such as tables extracted from PDFs.
  
- **Pydantic Models**: Pydantic schemas (e.g., `GetTopicSchema`, `GetQuestionSchema`, `EmptyArgsSchema`) are used to validate and structure the data, ensuring that any input or output adheres to the expected format.








