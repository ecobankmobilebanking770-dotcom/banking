# Verifybank Banking Portal API Documentation

## Overview
The Verifybank Banking Portal API provides a RESTful interface for managing various banking operations. This documentation outlines the key endpoints, authentication methods, request and response formats, email notification configurations, HTTPS security, and error handling mechanisms.

## Authentication
The API uses OAuth 2.0 for authentication. Clients must obtain an access token to interact with the API. The following steps outline the process:

1. **Request an Access Token**: Send a POST request to `/oauth/token` with the following parameters:
   - `client_id`: Your application client ID
   - `client_secret`: Your application client secret
   - `grant_type`: Set to `client_credentials`

2. **Receive the Token**: The response will include an access token, which must be included in the `Authorization` header of subsequent requests.
   - Example: `Authorization: Bearer YOUR_ACCESS_TOKEN`

## Endpoints

### 1. Create Account
- **URL**: `/api/accounts`
- **Method**: `POST`
- **Request Format**:
  ```json
  {
      "accountName": "string",
      "accountType": "string",
      "initialDeposit": number
  }
  ```
- **Response Format**:
  ```json
  {
      "accountId": "string",
      "status": "string"
  }
  ```

### 2. Get Account Details
- **URL**: `/api/accounts/{accountId}`
- **Method**: `GET`
- **Response Format**:
  ```json
  {
      "accountId": "string",
      "accountName": "string",
      "accountType": "string",
      "balance": number
  }
  ```

### 3. Transfer Funds
- **URL**: `/api/transfer`
- **Method**: `POST`
- **Request Format**:
  ```json
  {
      "fromAccountId": "string",
      "toAccountId": "string",
      "amount": number
  }
  ```
- **Response Format**:
  ```json
  {
      "status": "string",
      "transactionId": "string"
  }
  ```

## Email Notification System Configuration
To configure the email notification system:
- Set up SMTP server details in the environment variables:
  - `SMTP_HOST`
  - `SMTP_PORT`
  - `SMTP_USERNAME`
  - `SMTP_PASSWORD`
- Notifications are sent via email for:
  - Account creation
  - Fund transfers

## HTTPS Security
All API requests must be made over HTTPS to ensure data integrity and confidentiality. Ensure your server's SSL certificate is correctly configured.

## Error Handling
The API responds with appropriate HTTP status codes and error messages. Common error responses include:
- **400 Bad Request**: Invalid request parameters.
- **401 Unauthorized**: Authentication failed.
- **404 Not Found**: Resource not found.

The response structure for errors is:
```json
{
    "error": {
        "code": "string",
        "message": "string"
    }
}
```  

## Conclusion
This documentation provides a comprehensive overview of the Verifybank Banking Portal API. For any further queries, please contact support at support@verifybank.com.
