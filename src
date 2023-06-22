import pdfplumber
from transformers import pipeline
# nlp = pipeline("question-answering")
nlp = pipeline("question-answering", model="distilbert-base-cased-distilled-squad", revision="626af31")
# nlp2 = pipeline("summarization", model="facebook/bart-large-cnn", tokenizer="facebook/bart-large-cnn")
nlp2 = pipeline("summarization")
# nlp2 = pipeline("summarize")
# nlp2 = pipeline("summarization")
def convert_pdf_to_super(pdf_path):
    with pdfplumber.open(pdf_path) as pdf:
        text = ""
        for page in pdf.pages:
            text += page.extract_text()
        with open('super.txt' , 'r') as f:
          file_contents = f.read()
          if text in file_contents:
            print("file is already stored ")
          else:
              with open('super.txt', "a") as f:
                f.write(text + "\n")

def convert_text_to_super(text_path):
    with open(text_path , 'r') as txt:
        text = txt.read()
        with open('super.txt' , 'r') as f:
          file_contents = f.read()
          if text in file_contents:
            print("file is already stored ")
          else:
              with open('super.txt', "a") as f:
                f.write(text + "\n")

                
def convert_super_to_text(super_path):
    with open('super.txt', "r") as f:
        text = f.read()
    return text

def convert_file_to_text(super_path):
    with open(super_path , "r") as f:
        text = f.read()
    return text

inpu= input("Do you want to summmarize the text:(y or n)")
if inpu=='y':
    inp1 = input("Enter text file you want to summarize:(extension required)")
    text = convert_file_to_text(inp1)
    answer = nlp2(text)
    print("Summarizer:", answer[0]["summary_text"])

    # Preprocess and extract information from the text
inp=input("do you have pdf or a text file (Enter pdf if it's pdf and text if it's text)?")
if inp=="pdf" or inp=="PDF":
    #we will do 
    inp1 = input("enter your pdf name case sensitive with extension: ")
    convert_pdf_to_super(inp1)
    pdf_text = convert_super_to_text('super.txt')
    
    user_question = input("User: ")

    # Question answering using Hugging Face Transformers
    answer = nlp({
        "question": user_question,
        "context": pdf_text
    })

    print("Chatbot:", answer["answer"])
elif inp=="text" or inp=="Text":
    #we will do soon
    inp1 = input("enter your text name case sensitive with extension: ")
    convert_text_to_super(inp1)
    pdf_text = convert_super_to_text('super.txt')
    
    user_question = input("User: ")

    # Question answering using Hugging Face Transformers
    answer = nlp({
        "question": user_question,
        "context": pdf_text
    })

    print("Chatbot:", answer["answer"])
    
else: 
    print("please enter correct input bye...")
    
    

#ama problem evo j che ke append ma be tran var ama aai j jase
#bijo problem evo che ke jo super.txt delete thai gai ke hase j nai to pachi banavi padse


    # preprocessed_text = preprocess_text(pdf_text)
    # extracted_info = extract_information(preprocessed_text)
    #aa badhu pachi nakhi su mast banava
