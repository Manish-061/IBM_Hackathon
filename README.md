# 🚀 Duplicate File Remover 🚀

<p align="center">
  <img src="https://img.shields.io/badge/Java-11%2B-blue?style=for-the-badge&logo=java" alt="Java">
  <img src="https://img.shields.io/badge/Spring_Boot-2.5%2B-brightgreen?style=for-the-badge&logo=spring" alt="Spring Boot">
  <img src="https://img.shields.io/badge/React-17%2B-blueviolet?style=for-the-badge&logo=react" alt="React">
  <img src="https://img.shields.io/badge/TypeScript-4.5%2B-informational?style=for-the-badge&logo=typescript" alt="TypeScript">
  <img src="https://img.shields.io/badge/Maven-3.6%2B-critical?style=for-the-badge&logo=apache-maven" alt="Maven">
  <img src="https://img.shields.io/badge/Node.js-16%2B-green?style=for-the-badge&logo=node.js" alt="Node.js">
</p>

<p align="center">
  A powerful, intelligent duplicate file detection and removal application with cross-format content comparison, real-time scanning, and advanced categorization capabilities.
</p>

## 📖 Table of Contents

- [✨ Features](#-features)
- [🛠️ Installation](#-installation)
- [🚀 Quick Start](#-quick-start)
- [🏗️ Architecture](#️-architecture)
- [📖 Usage Guide](#-usage-guide)
- [🔧 Technical Details](#-technical-details)
- [🧪 Testing](#-testing)
- [🔄 API Endpoints](#-api-endpoints)
- [🤝 Contributing](#-contributing)
- [📝 License](#-license)

## ✨ Features

### 🔍 Advanced Duplicate Detection
- **Cross-Format Content Comparison**: Detect duplicates across different file formats (PDF ↔ DOCX, DOC ↔ TXT, etc.).
- **Metadata-Aware Hashing**: Ignores file metadata, focuses on actual content.
- **SHA256 Content Hashing**: Secure and accurate duplicate identification.
- **Real-Time Scanning**: Live progress tracking with detailed statistics.

### 📁 Smart File Categorization
- **Content-Based Detection**: Uses magic numbers and file signatures.
- **Custom Categorization Rules**: User-defined rules for file organization.
- **Multiple Categories**: Images, Documents, Videos, Audio, Applications, Archives, etc.
- **Persistent Settings**: Rules saved across sessions.

### 🎯 Cross-Format Support
- **PDF Files**: Full text extraction using Apache PDFBox.
- **DOCX Files**: Content extraction using Apache POI.
- **DOC Files**: Legacy Word format support.
- **Text Files**: Direct content reading.

### 💾 Persistent Settings Management
- **localStorage Integration**: Automatic settings persistence.
- **Import/Export**: JSON-based settings backup and restore.
- **Reset to Defaults**: Easy restoration of default settings.

### 📊 Comprehensive Logging & Analytics
- **Scan History**: Complete audit trail of all operations.
- **Activity Timeline**: Detailed step-by-step operation logs.
- **Statistics Dashboard**: Files processed, duplicates found, categories.
- **Real-Time Progress**: Live scanning progress with ETA.

### 🗂️ Advanced File Management
- **Bulk Operations**: Select and delete multiple files at once.
- **Directory Duplicates**: Detect duplicate directory structures.
- **Smart Selection**: Select all duplicates with one click.
- **Safe Deletion**: Confirmation dialogs and error handling.

## 🛠️ Installation

### Prerequisites
- **Java 11+** (for backend)
- **Node.js 16+** (for frontend)
- **Maven** (for backend build)

### Backend Setup
```bash
cd backend
mvn clean install
mvn spring-boot:run
```

### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

## 🚀 Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd IBM_Hackathon

# Start backend
cd backend && mvn spring-boot:run

# Start frontend (in new terminal)
cd frontend && npm run dev

# Access the application
open http://localhost:5173
```

## 🏗️ Architecture

### Frontend (React + TypeScript)
```
frontend/
├── src/
│   ├── components/          # React components
│   ├── services/           # API and business logic
│   └── types/             # TypeScript type definitions
```

### Backend (Spring Boot + Java)
```
backend/
├── src/main/java/com/duplicateremover/
│   ├── controller/         # REST API endpoints
│   ├── service/           # Business logic
│   └── model/             # Data models
```

## 📖 Usage Guide

1.  **Configure Settings**: Go to the Settings panel to customize categorization rules.
2.  **Start a Scan**: Choose a directory and start the scan.
3.  **Manage Duplicates**: Review the results and delete duplicates.

## 🔧 Technical Details

The system uses advanced content extraction to detect duplicates across different file formats.

```java
// PDF Content Extraction
private String extractPDFText(String filePath) throws IOException {
    try (PDDocument document = PDDocument.load(new File(filePath))) {
        PDFTextStripper stripper = new PDFTextStripper();
        return DigestUtils.sha256Hex(stripper.getText(document).getBytes("UTF-8"));
    }
}

// DOCX Content Extraction
private String extractDOCXText(String filePath) throws IOException {
    try (XWPFDocument document = new XWPFDocument(new FileInputStream(filePath))) {
        StringBuilder content = new StringBuilder();
        document.getParagraphs().forEach(p -> content.append(p.getText()).append("\n"));
        return DigestUtils.sha256Hex(content.toString().getBytes("UTF-8"));
    }
}
```

## 🧪 Testing

### Backend Testing
```bash
cd backend
mvn test
```

### Frontend Testing
```bash
cd frontend
npm test
```

## 🔄 API Endpoints

- `POST /api/scan`: Start a new scan
- `GET /api/scan/{scanId}`: Get scan results
- `DELETE /api/duplicates/{scanId}`: Delete duplicate files

## 🤝 Contributing

1.  **Fork the repository**
2.  **Create a feature branch**: `git checkout -b feature/amazing-feature`
3.  **Commit changes**: `git commit -m 'Add amazing feature'`
4.  **Push to branch**: `git push origin feature/amazing-feature`
5.  **Open a Pull Request**

## 📝 License

This project is licensed under the MIT License.

---

**Built with ❤️ for efficient file management and duplicate detection
