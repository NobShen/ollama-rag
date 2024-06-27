## Efficient Document Retrival using Ollama and PrivateGPT

This project aims to enhance document search and retrieval processes, ensuring privacy and accuracy in data handling.

### Getting Started

##### Step 1: Setup a Virtual Env

Python 3.10.12 is pre-installed on Ubuntu 22.04.  So cd to the directory where the new virtual environment is to be created.  Deactivate after use.

```bash
python3 -m venv venv
cd venv/bin
source activate
deactivate
```

##### Step 2: Install Dependencies using Pip

Clone the repository to venv created above.

```bash
sudo apt install python3-pip
git clone https://github.com/NobShen/ollama-rag.git
cd ollama-rag
pip install -r requirements.txt
```

##### Step 3: Ensure Ollama and Mistral are installed

Install ollama if you haven't already.  Head over to https://ollama.com/download

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Then pull mistral model.

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull mistral
```

Now you can look at ollama's vector database and see what it contains:

```bash
curl curl http://localhost:11434/api/embeddings -d '{
  "model": "mistral",
  "prompt": "Llamas are members of the camelid family"
}'
```

For a more detail look at where ollama stores the models, check out this issue:  https://github.com/ollama/ollama/issues/1737

##### Step 4: Create `source_documents` Folder and Add your Documents

```bash
mkdir source_documents
```

Supported file types:

- `.csv`: CSV,
- `.docx`: Word Document,
- `.doc`: Word Document,
- `.enex`: EverNote,
- `.eml`: Email,
- `.epub`: EPub,
- `.html`: HTML File,
- `.md`: Markdown,
- `.msg`: Outlook Message,
- `.odt`: Open Document Text,
- `.pdf`: Portable Document Format (PDF),
- `.pptx` : PowerPoint Document,
- `.ppt` : PowerPoint Document,
- `.txt`: Text file (UTF-8),

##### Step 5: Ingest Documents to Store in Vector Database for Query

```bash
python3 ingest.py
```

##### Step 6: Chat using PrivateGPT

```bash
python privateGPT.py
```

To use a different model try


```bash
ollama pull llama2:13b
MODEL=llama2:13b python privateGPT.py
```

##### Step 7: Clean up ollama memory to ingest new data

```bash
python privateGPT.py
```

To use a different model try


```bash
ollama pull llama2:13b
MODEL=llama2:13b python privateGPT.py
```
