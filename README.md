# SnapStore
Brief project description or tagline

## Table of Contents
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Clone the Repository](#clone-the-repository)
  - [Setting up the Client](#setting-up-the-client)
  - [Setting up the Server](#setting-up-the-server)
- [Branching Strategy](#branching-strategy)
- [Contributing](#contributing)
- [Project Requirements](#project-requirements)
- [Best Practices](#best-practices)
- [License](#license)

## Getting Started

### Prerequisites
Before you begin, ensure you have met the following requirements:
- Git: [Installation Guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Python (for server): [Python Downloads](https://www.python.org/downloads/)
- Node.js and npm (for client): [Node.js Downloads](https://nodejs.org/en/download/)

### Clone the Repository
To get started with the project, follow these steps:

```bash
#### Clone the repository to your local machine
git clone https://github.com/Arnold-Mwangi/SnapStore.git
```

```bash
cd SnapStore
```
### Setting up the Client
- The "client" folder contains the React app. To set up the client-side development environment:

## Navigate to the client folder
```bash
cd client
```

## Install dependencies
```bash
npm install
```

## Start the development server
```bash
npm start
```
- Access the React app at http://localhost:3000 in your web browser.

### Setting up the Server
- The "server" folder contains the Python Flask code. \
To set up the server-side development environment:

# Navigate to the server folder
```bash
cd server
```

# Create and activate a virtual environment (venv)
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

# Install Python dependencies
```bash
pip install -r requirements.txt
```

# Start the Flask server
```bash
python app.py
```
** Your server will be running at http://localhost:5000. **

## Branching Strategy
- We follow a branching strategy to manage our codebase:

`main`: The main branch, which represents the production-ready code.
`Ft-Client`: Branch for client-side development.
`Ft-Server`: Branch for server-side development.
- To create a new branch from one of these branches, use the following commands:

# Create and switch to a new branch
```bash
git checkout -b feature-branch main  # or Ft-Client, Ft-Server
git pull origin main # or Ft-Client, Ft-server considering you created a new branch fom it.

```

# Make changes, commit, and push to your branch
```bash
git add .
git commit -m "Your commit message"
git push origin feature-branch
```
