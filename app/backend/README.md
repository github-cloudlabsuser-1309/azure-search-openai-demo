# Backend Application Documentation

This document provides an overview of the backend application for the Azure OpenAI and Azure AI Search based RAG (Retrieval Augmented Generation) chat application.

## Overview

The backend is built using [Quart](https://quart.palletsprojects.com/), a Python asynchronous web framework, and implements the [AI Chat HTTP Protocol](https://aka.ms/chatprotocol) for communication with the frontend.

## Key Features

- Chat functionality with GPT-4 and GPT-3.5 models
- Document search and retrieval using Azure AI Search
- Support for GPT-4V (Vision) capabilities
- Authentication and access control integration
- Document upload and management
- Chat history persistence (browser-based and Cosmos DB)
- Speech input/output support
- Multi-language support
- Semantic search and query rewriting
- Support for vector search
- Monitoring and telemetry with Azure Monitor

## Project Structure

```
backend/
├── approaches/          # Different RAG implementation approaches
├── chat_history/        # Chat history implementations
├── core/               # Core functionality and helpers
├── prepdocslib/        # Document processing and indexing
├── app.py              # Main application file
├── main.py             # Application entry point
├── config.py           # Configuration management
├── requirements.txt    # Python dependencies
└── error.py           # Error handling
```

## Key Components

### Main Application (app.py)

The main application file contains:
- Route handlers for chat, document management, and configuration
- Client setup for Azure services
- Authentication and authorization middleware
- Configuration management
- Error handling

### Routes

- `/chat`: Handles chat interactions
- `/ask`: Single-turn Q&A endpoint
- `/upload`: Document upload endpoint
- `/config`: Application configuration endpoint
- `/auth_setup`: Authentication configuration endpoint

## Configuration

The application uses environment variables for configuration. Key configuration areas include:

### Azure Services
- Azure OpenAI Service
- Azure AI Search
- Azure Blob Storage
- Azure Cosmos DB (optional)
- Azure Speech Services (optional)

### Authentication
- Microsoft Entra ID integration
- Access control configuration
- User authentication settings

### Features
- Vector search
- Query rewriting
- Language selection
- Speech capabilities
- Chat history persistence
- User document upload

## Requirements

See `requirements.txt` for a complete list of dependencies. Key requirements include:

- azure-search-documents
- azure-storage-blob
- azure-identity
- azure-cosmos
- openai
- quart
- quart-cors
- azure-monitor-opentelemetry

## Development

### Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Set up environment variables:
   - Azure service configurations
   - Authentication settings
   - Feature flags

3. Run the development server:
   ```bash
   python main.py
   ```

### Deployment

The application can be deployed to:
- Azure App Service
- Azure Container Apps

Refer to the deployment documentation for detailed instructions.

## Monitoring

The application integrates with Azure Monitor and Application Insights for:
- Request tracking
- Performance monitoring
- Error logging
- OpenAI API usage tracking

## Security Features

- Authentication with Microsoft Entra ID
- Document-level access control
- Network security with private endpoints (optional)
- Request validation and sanitization

## Best Practices

1. Error Handling:
   - Use proper error responses
   - Implement retry mechanisms for Azure services
   - Log errors appropriately

2. Performance:
   - Use async/await for I/O operations
   - Implement proper caching
   - Monitor resource usage

3. Security:
   - Keep secrets in environment variables
   - Implement proper authentication
   - Validate user inputs

## Contributing

Refer to the main project's CONTRIBUTING.md file for contribution guidelines.

## Additional Resources

- [Customization Guide](../../docs/customization.md)
- [Production Guide](../../docs/productionizing.md)
- [Security Guide](../../docs/login_and_acl.md)
- [Feature Configuration](../../docs/deploy_features.md)
