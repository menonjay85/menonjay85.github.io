---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Chatbot, LLM, LangChain, PyQt5, Resume Assistance, Academic Support, Multilingual AI, RAG, NLP"

project:
  title: "Writing Support Chatbot"
  type: "Jekyll"
  url: "https://github.com/menonjay85/PIASN-hackathon"
  logo: "/assets/images/projects/ddl.webp"
  tech: "LangChain, LLaMA3, FAISS, PyQt5, RAG, Sentence Transformers, Web Scraping"
---

<p>International and first-year students often face hurdles in understanding U.S. academic writing standards, citation styles, and professional resume formats. To address this, my team developed a smart, multilingual chatbot tailored for students at <strong>Arizona State University (ASU)</strong>.</p>

<br>

<p>This AI-powered assistant offers writing and resume help based on real ASU resources. It adjusts its tone and language depending on each student’s fluency in English, and guides them through writing assignments, citation formats (APA, MLA, IEEE, Vancouver), and job preparation using a friendly, conversation-driven interface.</p>

<br>

<img class="img80" src="/assets/images/projects/c694decb-9a9f-4b4f-b057-a52a70c5c129.png" width="1400">
<center><h2>ASU Writing & Career Support Chatbot Demo (GUI built in PyQt5)</h2></center>

<br>

### 🔍 Key Features

- **Multilingual Language Detection**: Automatically detects the user's language and adapts its responses to enhance comfort and comprehension.
- **Citation Style Formatter**: Converts DOIs and article URLs into accurate citations using CrossRef API. Supports APA, MLA, IEEE, and Vancouver formats.
- **Resume Coaching Module**: For students looking to build their first resumes, especially helpful to those unfamiliar with U.S. job application standards.
- **Smart Query Router**: Classifies user intent using semantic similarity between the input and pre-labeled queries, routing them to either academic or career assistance modules.
- **Live Knowledge Retrieval (RAG)**: Uses FAISS vector index + scraped ASU resources to answer questions contextually, in real time.
- **Interactive Desktop App**: Built using PyQt5, enabling file uploads (.docx), document citation checks, and live conversation tracking.

<br>

### 🛠 Tech Stack

- **LangChain** – For building LLM-based workflows  
- **LLaMA3** – Large language model for personalized dialog  
- **FAISS** – Semantic search over university knowledgebase  
- **PyQt5** – Interactive desktop GUI  
- **Sentence Transformers** – For routing intent using embeddings  
- **BeautifulSoup** – Scraping official ASU help and library pages  
- **CrossRef API** – For real-world citation metadata retrieval  
- **Docx Parser** – Detects un-cited quotes in uploaded student documents

<br>

### 💡 Impact

<p>This chatbot empowers students who are new to the U.S. academic and professional systems. It supports both academic and career growth through real-time personalized assistance, particularly benefitting international and ESL (English as a Second Language) learners. Its modular, multi-agent architecture allows seamless switching between writing help and resume coaching.</p>

<br>

### 📁 Learn More or Try It

- 🔗 <a href="https://github.com/menonjay85/PIASN-hackathon" target="_blank"><strong>Source Code on GitHub</strong></a>  
<!-- - 🖼 <a href="https://drive.google.com/drive/folders/YOUR_FOLDER_LINK" target="_blank">Demo Presentation / Screenshots</a>   -->
- 💬 Try it locally using instructions in the repo’s README!

<br><br>

