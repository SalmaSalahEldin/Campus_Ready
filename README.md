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


