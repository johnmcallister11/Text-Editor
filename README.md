# QUBeditoron3000 – Cloud Text Editor Enhancement

This project was developed for the CSC3065 Cloud Computing module at Queen’s University Belfast. It builds on the existing QUBeditoron3000 system by introducing several improvements including new text functions, a reverse proxy, a monitoring tool, and stateful saving functionality.

The system is containerised using Docker, with each feature deployed as an independent service, and follows cloud-native principles such as microservice architecture and CI/CD.

## Project Overview

The base system provided a basic frontend and two backend services for word and character counting. I extended this by implementing additional functions, improving the reliability and structure of the frontend, creating a custom proxy router, developing a monitoring solution, and allowing for persistent saving and retrieval of text. A multi-cloud architectural design was also proposed.

## Technologies Used

- Docker
- Node.js, PHP, Python, Java, C#, Go
- Express, Flask, PHP-FPM
- CI/CD (GitLab Pipelines)
- SQLite (for saving text)
- Kubernetes (QPC deployment suggested)

## Implemented Features

### Additional Functions
Each of the following functions was implemented as a separate backend service:
- Vowel counter
- Comma counter
- Average word length calculator
- Palindrome detector

These functions communicate with the frontend via the proxy router.

### Improvements to Base System
- Handled asynchronous requests in the frontend to prevent overlap
- Added frontend error messages for failed backend responses
- Validated inputs on backend services
- Moved service endpoint configuration out of source code and into a config file

### Proxy Router
- Built a custom proxy in Node.js to handle all API requests from the frontend
- Allows dynamic configuration of endpoints
- Supports basic service discovery and routing logic

### Monitoring & Metrics
- Created a monitoring service to send periodic requests to all backends
- Logs response times and checks for expected outputs
- Designed to help detect downtime or service issues during testing

### Stateful Saving
- Built a save/load service using Flask and SQLite
- Users can save current editor text and receive a unique identifier
- Text can be restored by entering the ID

### Multi-Cloud Design
- Produced an architectural design showing how the editor could be deployed across multiple cloud providers
- Considered factors like fault tolerance, failover, and vendor-neutral routing

## How to Run

Clone the project and start the services using Docker Compose:
```bash
git clone https://github.com/yourusername/csc3065-editor.git
cd csc3065-editor
docker-compose up --build
