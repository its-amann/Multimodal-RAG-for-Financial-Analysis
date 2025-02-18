# 🌟 Multimodal RAG for Financial Analysis
<div align="center">
query = "You are a financial adviser. Answer based on the provided financial data."
<img src="_asserts/preparing%20images%20for%20retrival.png" alt="Project Banner" width="800"/>

[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-green.svg)](https://openai.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

## 📚 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Project Architecture](#-project-architecture)
- [RAG Pipeline](#-rag-pipeline)
- [Installation](#-installation)
- [Project Structure](#-project-structure)
- [How It Works](#-how-it-works)
- [Results & Visualization](#-results--visualization)
- [Contributing](#-contributing)
- [License](#-license)

## 🎯 Overview

This project implements a sophisticated Multimodal RAG (Retrieval-Augmented Generation) system designed for comprehensive financial analysis of corporate performance. The system can process and analyze multiple types of financial data sources, making it a versatile tool for investors, analysts, and financial professionals.

To demonstrate the system's capabilities, we've implemented a case study using Starbucks Corporation's Q3 2024 financial data, showcasing how the tool handles various data formats:

### 📊 Demonstration Data Sources

1. **Earnings Call Audio** (`starbucks-q3.mp3`):
   - Quarterly earnings call recording
   - Executive presentations and Q&A sessions
   - Strategic discussions and market insights
   - Forward-looking statements and guidance

2. **Financial Report** (`3Q24-Earnings-Release.pdf`):
   - Quarterly financial statements
   - Performance metrics and KPIs
   - Market analysis and trends
   - Supporting charts and visualizations

### 🔄 System Capabilities

The system's architecture enables processing of any company's financial data through:
- Automated audio transcription of earnings calls and presentations
- Intelligent PDF processing and image extraction
- Advanced embedding techniques for multimodal data
- Semantic search across all data formats
- Context-aware information retrieval and synthesis

This creates a versatile financial analysis tool that can:
- Process multiple data formats simultaneously
- Answer complex financial queries
- Cross-reference information across different sources
- Generate comprehensive insights with supporting evidence
- Adapt to different companies and financial contexts

<div align="center">
<img src="_asserts/image%20similarity%20computing.png" alt="System Overview" width="800"/>
</div>

The implementation demonstrates how modern AI techniques can revolutionize financial analysis by making it easier to process, understand, and derive insights from complex financial information across multiple formats and sources. While demonstrated with Starbucks' data, the system is designed to be adaptable to any company's financial documentation and reporting structure.

## 🚀 Key Features

- **Audio Transcription**: Converts earnings call recordings to text using Whisper
- **PDF Processing**: Extracts and processes financial reports and presentations
- **Multimodal Embeddings**: Generates embeddings for both text and images
- **Semantic Search**: Implements cosine similarity for relevant information retrieval
- **Intelligent Response Generation**: Uses GPT-4 for generating financial insights
- **Visual Analysis**: Processes financial charts and graphs from reports

## 🏗 Project Architecture

```mermaid
flowchart TD
    subgraph Input
        A[Input Sources] --> B[Audio File]
        A --> C[PDF Documents]
    end
    
    subgraph Processing
        B --> D[Whisper Transcription]
        C --> E[PDF to Image Conversion]
        D --> F[Text Chunks]
        E --> G[Image Processing]
    end
    
    subgraph Embeddings
        F --> H[Text Embeddings]
        G --> I[Image Embeddings]
        H --> J[(Vector Store)]
        I --> J
    end
    
    subgraph Query
        K[User Query] --> L[Query Embedding]
        L --> M{Similarity Search}
        J --> M
    end
    
    subgraph Output
        M --> N[Context Assembly]
        N --> O[GPT-4 Response]
    end

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style J fill:#bbf,stroke:#333,stroke-width:2px
    style M fill:#bfb,stroke:#333,stroke-width:2px
    style O fill:#ff9,stroke:#333,stroke-width:2px
```

## 🔄 RAG Pipeline

```mermaid
sequenceDiagram
    box User Interface
        participant User
    end
    box Backend System
        participant System
        participant Embeddings
    end
    box AI Processing
        participant LLM
    end

    User->>+System: Submit Query
    rect rgb(191, 223, 255)
        System->>+Embeddings: Generate Query Embedding
        Embeddings->>-System: Return Similar Content
    end
    rect rgb(255, 204, 204)
        System->>+LLM: Send Context + Query
        LLM->>-System: Generate Response
    end
    System->>-User: Return Answer

    note over System,LLM: Multimodal Processing
```

## 🛠 Installation

```bash
git clone https://github.com/yourusername/MuliModal-Rag-for-starbucks.git
cd MuliModal-Rag-for-starbucks
pip install -r requirements.txt
```

## 📁 Project Structure

```
MuliModal-Rag-for-starbucks/
├── _asserts/                  # Visualization assets
├── images/                    # Processed PDF images
├── transcript/                # Audio transcriptions
├── Capstone Project - Multimodal Data.ipynb  # Main notebook
├── requirements.txt           # Dependencies
├── starbucks-q3.mp3          # Audio input
└── 3Q24-Earnings-Release.pdf  # PDF input
```

## ⚙️ How It Works

1. **Audio Processing**
   <div align="center">
   <img src="_asserts/chuck%20size%20result%20preview.png" alt="Audio Processing" width="800"/>
   </div>
   
   - Transcribes audio using Whisper
   - Splits text into manageable chunks
   - Generates embeddings for each chunk

2. **PDF Processing**
   <div align="center">
   <img src="_asserts/saving%20the%20converted%20pdf%20pages%20to%20images%20output_follder%20%2C%20code%20%2B%20cell%20output.png" alt="PDF Processing" width="800"/>
   </div>
   
   - Converts PDF pages to images
   - Processes financial charts and tables
   - Creates embeddings for visual content

3. **Data Preprocessing & Encoding**
   <div align="center">
   <img src="_asserts/image%20encoding%20in%20base64.png" alt="Base64 Encoding" width="800"/>
   </div>
   
   - Converts images to base64 format for model input
   - Prepares data for CLIP model processing
   - Optimizes input format for OpenAI API

4. **Embedding Generation**
   <div align="center">
   <img src="_asserts/seeing%20the%20shape%20of%20the%20image%20embeddings.png" alt="Embedding Shape" width="800"/>
   <img src="_asserts/image%20embedding.png" alt="Embedding Process" width="800"/>
   </div>
   
   - Uses CLIP model for image embeddings
   - Employs Sentence Transformers for text
   - Maintains vector consistency

5. **Similarity Search**
   <div align="center">
   <img src="_asserts/cosine%20similarities.png" alt="Similarity Search" width="800"/>
   </div>
   
   - Implements cosine similarity
   - Retrieves relevant content
   - Combines multimodal results

6. **Response Generation**
   <div align="center">
   <img src="_asserts/query%20output%20genrated%20by%20the%20model.png" alt="Response Generation" width="800"/>
   </div>
   
   - Assembles retrieved context
   - Generates comprehensive answers
   - Provides financial insights

## 📊 Results & Visualization

The system demonstrates impressive capabilities in analyzing Starbucks' financial performance through multimodal data processing:

### 🎯 Key Achievements

1. **Audio Analysis**
   - Successfully transcribed Q3 earnings call
   - Processed 142 text chunks with 512-dimensional embeddings
   - Achieved high transcription accuracy with Whisper model

2. **Visual Processing**
   - Converted 17 PDF pages to high-quality images
   - Generated consistent 512-dimensional CLIP embeddings
   - Maintained visual context through document processing

3. **Retrieval Performance**
   - Achieved cosine similarity scores > 0.90 for relevant content
   - Top-5 audio chunk similarities: 0.90-0.91 range
   - Effective multimodal context assembly

### 🖼️ Image Preprocessing for OpenAI

A crucial step in our pipeline is preparing images for the OpenAI model. This involves:

<div align="center">
<img src="_asserts/preparing%20images%20for%20retrival.png" alt="Image Preprocessing" width="800"/>
</div>

**Process Highlights:**
- Converting images to base64 format
- Optimizing image resolution and quality
- Preparing batch processing for multiple images
- Ensuring proper formatting for API input
- Managing memory efficiency for large documents

This preprocessing step is essential for:
- Maintaining image quality
- Optimizing API performance
- Ensuring accurate visual analysis
- Enabling efficient multimodal processing

### 📈 Example Query Analysis

#### Query
```
How is the company doing financially?
```

#### System Response
<div align="center">
<img src="_asserts/query%20output%20genrated%20by%20the%20model.png" alt="Financial Analysis Output" width="800"/>
</div>

The system generated a comprehensive analysis that included:

**Financial Metrics:**
- Q3 total company revenue: $9.1 billion (↑1% YoY, ↑6% QoQ)
- Global comparable store sales declined 3% year over year
- Operating margins contracted by 70 basis points to 16.7%
- Earnings per share: 93 cents

**Regional Performance:**
- North America: -2% Comcro
- China: -14% Comcro
- Strong performance in Japan
- International challenges, particularly in China

**Strategic Insights:**
- Implementation of three-part action plan
- Operational improvements in US stores
- Enhanced customer experience initiatives
- Digital engagement metrics

**Future Outlook:**
- Planned improvements in store operations
- Strategic investments in partner hours
- Expansion plans in tier 2 and tier 3 cities
- Technology deployment roadmap

The system successfully combined information from:
- Earnings call audio transcription
- Financial statements and metrics
- Visual data from presentations
- Management commentary and guidance

This demonstrates the system's ability to:
1. Process complex financial queries
2. Synthesize information from multiple sources
3. Present structured, comprehensive analysis
4. Provide both quantitative and qualitative insights

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---
<div align="center">
Made with ❤️ for financial analysis
</div> 
