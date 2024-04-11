# Getting Started

Welcome to LeadsCalendar! This guide will help you set up LeadsCalendar on your system. Follow these steps to get started.

## Prerequisites

Before diving into the setup, please ensure you have the following:

- **Internet Connection**: Required for accessing LeadsCalendar's web interface and its integrations.
- **Web Browser**: Chrome, Firefox, Safari, or Edge for the best experience.
- **API Accounts**: You'll need accounts and API keys from:
  - Google (for Google Calendar API)
  - PayPal (for PayPal REST API)
  - Binance (for Binance Pay API)

## Installation Guide

### Step 1: Obtain API Keys

1. **Google Calendar API**:
   - Visit [Google Developers Console](https://console.developers.google.com/).
   - Create a project and enable Google Calendar API.
   - Navigate to 'Credentials' to generate your API key.

   > Note: Store your Google API key securely, as you'll need to input it into the LeadsCalendar configuration file.

2. **PayPal REST API**:
   - Access [PayPal Developer Portal](https://developer.paypal.com/).
   - Under 'My Apps & Credentials', create an app to get your Client ID and Secret.

   > Note: Your PayPal Client ID and Secret are crucial for payment processing. Keep them secure.

3. **Binance Pay API**:
   - Go to [Binance Pay for Developers](https://developers.binance.com/docs/binance-pay/introduction).
   - Follow the registration process to get your API Key and Secret.

   > Note: Like with other API keys, your Binance API Key and Secret must be stored securely.

### Step 2: Configure LeadsCalendar

- **Clone the Repository**:
  - Clone the LeadsCalendar code repository to your local machine or server.

  ```bash
  git clone https://github.com/yourrepository/LeadsCalendar.git
  cd LeadsCalendar
  ```

- **Install Dependencies**:
  - Depending on your project setup, you might need to install dependencies. If you're using npm, you can run:

  ```bash
  npm install
  ```

- **Environment Configuration**:
  - Find the configuration file (e.g., `.env` or `config.json`) in the LeadsCalendar directory.
  - Enter your API keys for Google Calendar, PayPal, and Binance Pay as obtained in Step 1.

  ```json
  {
    "GOOGLE_API_KEY": "your_google_api_key_here",
    "PAYPAL_CLIENT_ID": "your_paypal_client_id_here",
    "PAYPAL_SECRET": "your_paypal_secret_here",
    "BINANCE_API_KEY": "your_binance_api_key_here",
    "BINANCE_SECRET": "your_binance_secret_here"
  }
  ```

### Step 3: Launch LeadsCalendar

- **Start the Application**:
  - Use your server software or a command line tool to start the LeadsCalendar application. For example, if you're using node.js, you might run:

  ```bash
  npm start
  ```

- **Access LeadsCalendar**:
  - Open your web browser and go to the URL where LeadsCalendar is hosted.

Congratulations! You have successfully set up LeadsCalendar. You're now ready to explore its features, create events, and integrate payments seamlessly.
