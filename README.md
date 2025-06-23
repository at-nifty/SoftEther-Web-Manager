# SoftEther Web Manager
SoftEther Web Manager is a web-based application designed to provide intuitive GUI management for SoftEther VPN Server. It aims to offer a "software-less" and multi-platform solution for managing SoftEther VPN Server, especially those running on Linux environments.

This MVP (Minimum Viable Product) version focuses on establishing the core connection and authentication functionalities, along with basic information retrieval. Future versions will progressively implement a comprehensive set of management features, aiming to match the capabilities of the Windows server manager.

## 🚀 Key Features
Web-based GUI Management: Manage your SoftEther VPN Server from any OS (Windows, macOS, Linux, tablets, etc.) using just a web browser. No specific native application installation is required on the client side.
"Software-less" Operation: No need to install any dedicated management software on your client device.
Linux VPN Server Focused: Optimized for managing SoftEther VPN Server (v4.44 anticipated) running on Linux environments.
JSON-RPC API Utilization: Directly leverages the SoftEther VPN Server's JSON-RPC API, eliminating the need for vpncmd text parsing, leading to robust and stable communication.
Security Conscious: The SoftEther VPN Server's administrative password is securely handled by the web application's backend.
## ⚙️ Technology Stack
Frontend: React (with Vite and Tailwind CSS)
Backend: Node.js (with Express)
API Communication: SoftEther VPN Server JSON-RPC API
Protocol: HTTPS (supports self-signed SSL certificates)
Authentication: Uses the SoftEther VPN Server's "administrator password" (session management handled by the web app)
## 📦 Project Structure
The main file structure of the project is as follows:
```
softether-web-manager/
├── config.json               # VPN Server host, port, TLS settings, etc.
├── vpnclient.js              # SoftEther JSON-RPC API wrapper (for backend)
├── index.js                  # Express server entry point
├── frontend/                 # React + Vite frontend application
│   ├── public/
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── pages/            # Page components
│   │   ├── App.jsx           # Main application component
│   │   ├── main.jsx          # Frontend entry point
│   │   └── index.css         # Tailwind CSS base styles
│   ├── index.html            # Frontend HTML entry point
│   ├── package.json          # Frontend dependencies
│   └── vite.config.js        # Vite configuration
├── package.json              # Backend dependencies (npm scripts, etc.)
├── .gitignore                # Files to be ignored by Git
└── README.md                 # This document
```
## 🛠️ Development Environment Setup
Prerequisites
Node.js (LTS version recommended) and npm/yarn
SoftEther VPN Server (v4.44 recommended) running with JSON-RPC API enabled.
Administrator password for API access must be set.
Confirm the port number (e.g., 443, 5555) on which the API is listening.
Setup Steps
Clone the repository:

```Bash

git clone https://github.com/your-username/softether-web-manager.git
cd softether-web-manager
Install backend dependencies:
npm install
```
# How to install
Install frontend dependencies:

```Bash

cd frontend
npm install
```
# Other install
```Bash
cd ..
Configure config.json:
Create a config.json file and set the SoftEther VPN Server connection information.
```
```JSON

{
  "vpnServerHost": "your_vpn_server_ip_or_hostname",
  "vpnServerPort": 443,      // SoftEther VPN Server's JSON-RPC API port
  "webAppPort": 3000,        // Port for this Web Manager application
  "insecure": true           // Set to true to accept self-signed SSL certificates (for development)
}
```
Note: insecure: true is for development only. For production environments, it is strongly recommended to use a trusted SSL certificate.

## ▶️ How to Run
Verify SoftEther VPN Server:
Ensure your SoftEther VPN Server is running and its JSON-RPC API is enabled as configured.

Start the Web Manager:
From the project's root directory, run the following command:

```Bash

npm start
```
# Or node index.js
This will launch both the Express backend server and the React frontend.

Access in Web Browser:
Open your web browser and navigate to https://localhost:<webAppPort> (e.g., https://localhost:3000).

## 🔐 Security Considerations
At the MVP stage, the following security policies are in place:

VPN Server Administrator Password: Input by the user on the login screen, it's held temporarily only during the session by the backend. No persistent storage is performed.
Session Management: The web application manages its own login sessions and holds the sessionId returned by the SoftEther API.
Self-Signed SSL Certificates: For development simplicity, config.insecure = true allows self-signed certificates. However, for production, the use of official certificates is highly recommended.
Web App's Own Login Authentication: Currently, the SoftEther VPN Server's administrator password serves as the login password for the web application. Future versions will implement independent user management and authentication for the web app.
## 🗺️ Roadmap
After the MVP release, the following features are planned for phased implementation. The goal is to replicate the functionality and user experience of the Windows SoftEther VPN Server Manager on the web.

Create/Delete Virtual HUBs
Display users within a HUB
Add/Delete/Edit users
Retrieve/Disconnect sessions
View connection logs
Backup/Restore settings
Advanced server settings (Listeners, SecureNAT, L3 Switch, etc.)
More granular authentication and authorization features
Multi-language support
Further UI/UX improvements
