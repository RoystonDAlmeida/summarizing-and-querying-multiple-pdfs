# Summarizing and Querying Multiple Papers with LangChain

## 📝 Overview

This project demonstrates how to leverage LangChain to efficiently summarize and query multiple research papers, enhancing research productivity through advanced natural language processing techniques.

## ✨ Features

- Summarize multiple PDF documents
- Query across multiple papers using natural language
- Save summaries to text files
- Configurable model parameters

## 🛠 Prerequisites

- Python 3.7+
- LangChain library
- ChatGroq API Key
- PyPDF2 library

## 🚀 Installation

### Clone the Repository

```bash
git clone git@github.com:RoystonDAlmeida/summarizing-and-querying-multiple-pdfs.git
cd summarizing-and-querying-multiple-pdfs/
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Set ChatGroq API Key

```bash
GROQ_API_KEY = 
```

## 💻 Usage

### Summarizing Papers

```python
def summarize_pdfs_from_folder(pdfs_folder):
    summaries = []
    for pdf_file in glob.glob(pdfs_folder + "/*.pdf"):
	loader = PyPDFLoader(pdf_file)
	docs = loader.load_and_split()
	chain = load_summarize_chain(llm, chain_type="map_reduce")
	summary = chain.run(docs)
	print("Summary for: ", pdf_file)
	print(summary)
	print("\n")
	summaries.append(summary)
    
    return summaries
```

```python
summaries = summarize_pdfs_from_folder("./pdfs")
```

### Saving Summaries

```python
# Save all summaries into one .txt file
with open("summaries.txt", "w") as f:
    for summary in summaries:
	f.write(summary+"\n"*3)
```

### Querying Papers

```python
query = "What are the key trends on LLM from 2018 to 2023?"
# Invoke the index vector store using the query
index.query(query)
```
	

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 🔒 License

MIT License - see [LICENSE](https://mit-license.org/) for details

## 🙏 Acknowledgments

- LangChain
- ChatGroq

## 🛡 Troubleshooting

- Verify ChatGroq API key
- Check dependency installations
- Ensure PDF files are readable
