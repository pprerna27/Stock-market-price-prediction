pip install selenium pymupdf pandas
import fitz  # PyMuPDF
import pandas as pd
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
import time

# Set up Selenium WebDriver
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))

# URL of the PDF to be downloaded
pdf_url = 'URL_OF_THE_PDF'

# Download the PDF
driver.get(pdf_url)
time.sleep(5)  # Wait for the PDF to download

# Assuming the PDF is downloaded to the default download directory
pdf_path = 'path_to_downloaded_pdf.pdf'

# Close the browser
driver.quit()

# Open the PDF file
pdf_document = fitz.open(pdf_path)

# Extract text from each page
text = ""
for page_num in range(len(pdf_document)):
    page = pdf_document.load_page(page_num)
    text += page.get_text()

# Close the PDF document
pdf_document.close()

# Process the extracted text and store it in a DataFrame
# This example assumes the text is structured in a way that can be split into rows and columns
data = [line.split() for line in text.split('\n') if line.strip() != '']
df = pd.DataFrame(data)

# Display the DataFrame
print(df)

2.......pip install pytesseract pdf2image pandas
import pytesseract
from pdf2image import convert_from_path
import pandas as pd

# Path to the PDF file
pdf_path = 'path_to_your_pdf.pdf'

# Convert PDF to a list of images
images = convert_from_path(pdf_path)

# Initialize an empty list to hold the extracted text
extracted_text = []

# Loop through each image (page) and extract text using Tesseract
for image in images:
    text = pytesseract.image_to_string(image)
    extracted_text.append(text)

# Combine all extracted text into a single string
all_text = "\n".join(extracted_text)

# Process the extracted text and store it in a DataFrame
# This example assumes the text is structured in a way that can be split into rows and columns
data = [line.split() for line in all_text.split('\n') if line.strip() != '']
df = pd.DataFrame(data)

# Display the DataFrame
print(df)

3
import pytesseract
from pdf2image import convert_from_path
import pandas as pd

# Path to the PDF file
pdf_path = 'path_to_your_pdf.pdf'

# Convert PDF to a list of images
images = convert_from_path(pdf_path)

# Initialize an empty list to hold the extracted text
extracted_text = []

# Loop through each image (page) and extract text using Tesseract
for image in images:
    text = pytesseract.image_to_string(image)
    extracted_text.append(text)

# Combine all extracted text into a single string
all_text = "\n".join(extracted_text)

# Process the extracted text and store it in a DataFrame
# This example assumes the text is structured in a way that can be split into rows and columns
data = [line.split() for line in all_text.split('\n') if line.strip() != '']
df = pd.DataFrame(data)

# Display the DataFrame
print(df)


