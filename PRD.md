# Product Requirements Document (PRD) – Custom Webhook Response API

## 1. Objective
Develop a Zapier app that replicates **Webhooks by Zapier** but allows the user to specify a custom response payload. Users authenticate via basic authentication (username and password) and configure other settings inside Zapier.

## 2. Core Features
- **Webhook Endpoint**
  - Accept incoming HTTP requests (POST preferred; GET optional).
  - Respond with a user-defined payload (JSON or plain text).
  - Support configurable HTTP status code and headers.
- **Basic Authentication**
  - Users create a username and password (stored securely—hash + salt).
  - Every webhook request requires these credentials via HTTP Basic Auth.
- **Minimal User Interface**
  - Provide only a registration page for creating/managing credentials.
  - All other user interaction occurs within Zapier during Zap configuration.
- **Zapier Integration**
  - Expose triggers/actions for:
    - **Trigger**: Receive webhook calls.
    - **Action**: Send data and return the custom response to Zapier.
  - Users map the response body, headers, and status code inside Zapier.
- **Rate Limiting & Security**
  - Enforce HTTPS.
  - Apply reasonable limits on payload size and request frequency to prevent abuse.

## 3. Clarifications
- **Single Response Template**: Each user maintains one configurable response. There is no library of multiple templates.
- **Supported Formats**: Responses are limited to JSON or plain text.
- **Normal Limits**: Request frequency and payload size follow best-practice norms for webhook usage.

## 4. Non‑Goals
- No advanced content types (XML, form-encoded) or multiple saved responses.
- No complex dashboards or additional UI beyond credential management.

## 5. Success Metrics
- Users can register credentials, set up a Zap, and receive custom responses matching the configured body, headers, and status code.
- Authentication works reliably during Zap execution.
- All requests conform to rate limits without exceeding payload restrictions.
