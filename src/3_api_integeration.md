# API Integration Guides

Integrating LeadsCalendar with Google Calendar, PayPal, and Binance Pay APIs allows for seamless event creation and payment processing. This chapter details the steps required for each API integration.

## Google Calendar API Integration

### Overview

The Google Calendar API enables LeadsCalendar to create and manage events directly on a user's calendar.

### Setup and Authentication

1. **Enable the API**:
   - Visit the [Google Developers Console](https://console.developers.google.com/).
   - Select or create a new project.
   - Navigate to 'Library', find the Google Calendar API, and enable it for your project.

2. **Create Credentials**:
   - In the 'Credentials' tab, click 'Create Credentials' > 'OAuth client ID'.
   - Follow the prompts, selecting 'Web application' as the application type.
   - Add your application's URL to the 'Authorized redirect URIs'.

3. **Obtain OAuth 2.0 Credentials**:
   - After creating the OAuth client, you'll receive your client ID and client secret.

### Creating Events

Use the OAuth 2.0 credentials to authenticate API requests. Here's a basic example in JavaScript for creating an event:

```javascript
const {google} = require('googleapis');
const calendar = google.calendar('v3');

async function createEvent(auth) {
  const event = {
    summary: 'LeadsCalendar Event',
    start: {
      dateTime: '2024-05-01T09:00:00-07:00',
      timeZone: 'America/Los_Angeles',
    },
    end: {
      dateTime: '2024-05-01T17:00:00-07:00',
      timeZone: 'America/Los_Angeles',
    },
  };

  try {
    const response = await calendar.events.insert({
      auth: auth,
      calendarId: 'primary',
      resource: event,
    });
    console.log('Event created: %s', response.data.htmlLink);
  } catch (error) {
    console.error('Error creating event', error);
  }
}
```

## PayPal REST API Integration

### Overview

The PayPal REST API facilitates secure payment processing for LeadsCalendar events.

### Setup and Authentication

1. **Create a PayPal Developer Account**:
   - Sign up or log in at [PayPal Developer](https://developer.paypal.com/).

2. **Create an App**:
   - Navigate to 'Dashboard' > 'My Apps & Credentials'.
   - Create a new app to receive your sandbox and live API credentials.

### Processing Payments

Here's how to initiate a payment process using the PayPal SDK:

```javascript
const paypal = require('@paypal/checkout-server-sdk');

async function createPayment() {
  const request = new paypal.orders.OrdersCreateRequest();
  request.prefer("return=representation");
  request.requestBody({
    intent: 'CAPTURE',
    purchase_units: [{
      amount: {
        currency_code: 'USD',
        value: '1.00',
      },
    }],
  });

  try {
    const response = await client.execute(request);
    console.log('Order ID:', response.result.id);
  } catch (err) {
    console.error(err);
  }
}
```

## Binance Pay API Integration

### Overview

Integrate Binance Pay to accept cryptocurrency payments for LeadsCalendar events.

### Setup and Authentication

1. **Register as a Merchant**:
   - Complete the merchant registration process at [Binance Pay](https://pay.binance.com/).

2. **Obtain API Keys**:
   - Access your merchant dashboard to generate API keys.

### Processing Cryptocurrency Payments

Implementing a crypto payment involves creating a payment request and handling the callback:

```javascript
const axios = require('axios');

async function createCryptoPayment() {
  const data = {
    merchantId: 'your_merchant_id',
    prepayId: 'your_prepay_id',
  };

  try {
    const response = await axios.post('https://binance.com/api/v1/payments', data, {
      headers: { 'X-API-KEY': 'your_api_key' },
    });
    console.log('Payment initiated:', response.data);
  } catch (error) {
    console.error('Payment initiation failed:', error);
  }
}
```
