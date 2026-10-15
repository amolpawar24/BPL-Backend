# BPL Official — Backend

**Backend API for the Bhalawani Premier League (BPL) Official application.**

BPL Official is a cricket tournament platform designed to bring tournament-related information and features into one digital experience. This repository contains the backend application built with Node.js, Express.js, TypeScript, and MongoDB.

The backend follows a modular architecture to organize API routing, business logic, database models, payment processing, player management, and shared utilities.

**Live Frontend:** https://bpl-official2026.netlify.app/

**Repository:** https://github.com/amolpawar24/BPL-Backend

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Available Scripts](#available-scripts)
- [Architecture](#architecture)
- [API Structure](#api-structure)
- [Database Configuration](#database-configuration)
- [Player Module](#player-module)
- [Payment Module](#payment-module)
- [Uploads Module](#uploads-module)
- [Error Handling](#error-handling)
- [Logging and Utilities](#logging-and-utilities)
- [Frontend Integration](#frontend-integration)
- [Security Best Practices](#security-best-practices)
- [Build and Deployment](#build-and-deployment)
- [Troubleshooting](#troubleshooting)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## Overview

The BPL Backend provides the server-side foundation for the BPL Official cricket tournament application.

It is developed using TypeScript and Express.js, with MongoDB as the database and Mongoose for data modeling. Its modular structure separates application configuration, API routes, controllers, services, models, middleware, and reusable utilities.

The project also includes dependencies for media management, email delivery, file uploads, HTTP security, request logging, and Razorpay payment integration.

### Project Goals

- Build a maintainable backend for the BPL Official application.
- Organize API endpoints using versioned routing.
- Separate business logic from HTTP request handling.
- Support player and match-related functionality.
- Integrate payment processing through Razorpay.
- Provide reusable API responses and error-handling utilities.
- Support future expansion of tournament features.

---

## Features

### Backend Foundation

- REST API development with Express.js.
- TypeScript for structured, type-safe development.
- Modular and feature-based project architecture.
- Versioned API route organization.
- Centralized environment configuration.
- MongoDB integration using Mongoose.

### API and Error Handling

- Centralized API error utility.
- Global error-handling middleware.
- Not-found route handling.
- Asynchronous controller error handling.
- Standardized API response utility.
- Reusable pagination utility.

### Player Management

- Dedicated player module.
- Player model and data access structure.
- Player controllers, routes, and services.

### Payment Integration

- Razorpay configuration.
- Dedicated payment module.
- Payment controllers, models, routes, and services.
- Payment-related TypeScript types.
- Shared Razorpay utility functions.

### Additional Integrations

- Cloudinary for media management.
- Multer for file upload handling.
- Nodemailer for email delivery.
- Helmet for HTTP security headers.
- CORS for cross-origin request configuration.
- Morgan for HTTP request logging.
- dotenv for environment variable management.

*Feature availability depends on the implementation and configuration of each module. A dependency being installed does not necessarily mean its associated functionality is complete.*

---

## Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | Backend web framework |
| TypeScript | Type-safe application development |
| MongoDB | NoSQL database |
| Mongoose | MongoDB object modeling |
| Razorpay | Payment gateway integration |
| Cloudinary | Media storage and management |
| Multer | File upload handling |
| Nodemailer | Email delivery |
| Helmet | HTTP security headers |
| CORS | Cross-origin resource sharing |
| Morgan | HTTP request logging |
| dotenv | Environment variable management |
| ts-node | TypeScript execution |
| ts-node-dev | Development server with automatic restart |
| TypeScript Compiler | Production compilation |
| Chalk | Terminal output styling |

---

## Project Structure

The backend follows a modular architecture that separates application configuration, versioned API routing, feature modules, middleware, and reusable utilities.

```text
bpl-backend/
│
├── src/
│   │
│   ├── api/
│   │   └── v1/
│   │       └── routes.ts
│   │
│   ├── config/
│   │   ├── db.ts
│   │   ├── dns.ts
│   │   ├── env.ts
│   │   ├── logger.ts
│   │   └── razorpay.ts
│   │
│   ├── middlewares/
│   │   ├── globalErrorHandler.ts
│   │   └── notFoundHandler.ts
│   │
│   ├── modules/
│   │   ├── matches/
│   │   │
│   │   ├── payment/
│   │   │   ├── payment.controller.ts
│   │   │   ├── payment.model.ts
│   │   │   ├── payment.routes.ts
│   │   │   ├── payment.service.ts
│   │   │   └── payment.types.ts
│   │   │
│   │   ├── player/
│   │   │   ├── player.controller.ts
│   │   │   ├── player.model.ts
│   │   │   ├── player.routes.ts
│   │   │   └── player.service.ts
│   │   │
│   │   └── uploads/
│   │
│   ├── shared/
│   │   └── utils/
│   │       └── razorpay.ts
│   │
│   ├── utils/
│   │   ├── apiError.ts
│   │   ├── catchAsynch.ts
│   │   ├── getRoutes.ts
│   │   ├── methodTag.ts
│   │   ├── pagination.ts
│   │   ├── printBanner.ts
│   │   └── sendResponse.ts
│   │
│   ├── app.ts
│   └── server.ts
│
├── dist/                  # Generated build output
├── .env                   # Local environment configuration
├── .env.example           # Environment variable template
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
└── README.md
```

### Directory Responsibilities

| Directory / File | Responsibility |
|---|---|
| `src/api/v1/` | Versioned API route registration |
| `src/config/` | Database, DNS, environment, logging, and Razorpay configuration |
| `src/middlewares/` | Global error handling and not-found responses |
| `src/modules/matches/` | Match-related functionality |
| `src/modules/payment/` | Payment routes, controllers, models, services, and types |
| `src/modules/player/` | Player routes, controllers, models, and services |
| `src/modules/uploads/` | Upload-related functionality |
| `src/shared/utils/` | Shared Razorpay utilities |
| `src/utils/` | Common error, response, pagination, route, and asynchronous utilities |
| `src/app.ts` | Express application setup |
| `src/server.ts` | Server entry point |

The `matches/` and `uploads/` directories are included according to the supplied source tree. Their specific functionality should be documented as their implementation develops.

The `dist/` directory is generated by the TypeScript build and should generally not be committed when it is reproducible from source.

---

## Prerequisites

Before setting up the project, install:

- **Node.js:** A supported LTS version compatible with the project's dependencies.
- **npm:** Included with Node.js.
- **MongoDB:** Local MongoDB or MongoDB Atlas.
- **Git:** For version control.
- **Visual Studio Code:** Recommended editor.

Depending on which integrations you use, you may also need Cloudinary, SMTP, and Razorpay accounts.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/amolpawar24/BPL-Backend.git
```

### 2. Navigate to the Project

```bash
cd BPL-Backend
```

### 3. Install Dependencies

```bash
npm install
```

### 4. Configure Environment Variables

Create a `.env` file in the project root.

Use the environment variable template below as a starting point. The exact variable names must match those used in your source code.

### 5. Start the Development Server

```bash
npm run dev
```

This runs the TypeScript server entry point:

```text
src/server.ts
```

The `ts-node-dev` process restarts the development server when supported source files change.

### 6. Build the Application

```bash
npm run build
```

This executes the TypeScript compiler using `tsconfig.json`.

### 7. Start the Production Server

```bash
npm start
```

This runs the compiled server:

```text
dist/server.js
```

Build the application before starting it in production.

---

## Environment Variables

Environment variables allow the application to access configuration and credentials without hardcoding secrets into source files.

### Example `.env.example`

```env
# Application
NODE_ENV=development
PORT=5000

# Database
MONGODB_URI=

# Frontend / CORS
CORS_ORIGIN=https://bpl-official2026.netlify.app

# Cloudinary
CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=

# Email / SMTP
SMTP_HOST=
SMTP_PORT=
SMTP_USER=
SMTP_PASS=
EMAIL_FROM=

# Razorpay
RAZORPAY_KEY_ID=
RAZORPAY_KEY_SECRET=
```

These names are illustrative. Check `src/config/env.ts`, `src/config/db.ts`, `src/config/razorpay.ts`, and the integration code to confirm the actual environment variables required by the application.

Do not add real credentials to `.env.example`.

### Environment Variable Reference

| Variable | Purpose |
|---|---|
| `NODE_ENV` | Application environment |
| `PORT` | Server listening port |
| `MONGODB_URI` | MongoDB connection string |
| `CORS_ORIGIN` | Allowed frontend origin |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary account name |
| `CLOUDINARY_API_KEY` | Cloudinary API key |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret |
| `SMTP_HOST` | SMTP server hostname |
| `SMTP_PORT` | SMTP server port |
| `SMTP_USER` | SMTP username |
| `SMTP_PASS` | SMTP password or app password |
| `EMAIL_FROM` | Sender email address |
| `RAZORPAY_KEY_ID` | Razorpay key identifier |
| `RAZORPAY_KEY_SECRET` | Razorpay secret key |

Configure only the variables used by your implementation.

---

## Available Scripts

The project defines the following npm scripts:

| Command | Description |
|---|---|
| `npm run dev` | Starts the TypeScript development server |
| `npm run build` | Compiles TypeScript |
| `npm start` | Starts the compiled production server |

The scripts are configured in `package.json`.

```json
{
  "scripts": {
    "dev": "ts-node-dev --respawn src/server.ts",
    "build": "tsc",
    "start": "node --enable-source-maps dist/server.js"
  }
}
```

---

## Architecture

The project uses a modular, feature-based backend architecture.

### Request Lifecycle

A typical API request follows this conceptual flow:

```text
Client Request
      |
      v
Express Application
      |
      v
API Route Registration
      |
      v
Feature Route
      |
      v
Controller
      |
      v
Service / Business Logic
      |
      v
Mongoose Model
      |
      v
MongoDB
      |
      v
Standardized API Response
```

The exact flow depends on the implementation of individual routes and services.

### Architectural Principles

- Keep route definitions separate from business logic.
- Keep controllers focused on HTTP request and response handling.
- Use services for reusable business operations.
- Use Mongoose models for database interactions.
- Centralize application configuration.
- Reuse common API response and error-handling utilities.
- Organize new features inside their respective modules.

---

## API Structure

The project includes versioned API routing under:

```text
src/api/v1/routes.ts
```

This provides a place to register API routes for version 1.

The payment module contains:

```text
src/modules/payment/payment.routes.ts
```

The player module contains:

```text
src/modules/player/player.routes.ts
```

The actual API base path and individual endpoints depend on how these files are registered in `app.ts` and `routes.ts`.

### API Documentation

Document implemented endpoints using a table like the following when their paths and HTTP methods are confirmed:

| Method | Endpoint | Description |
|---|---|---|
| GET | To be documented | Retrieve resource data |
| POST | To be documented | Create or process a resource |
| PATCH | To be documented | Update an existing resource |
| DELETE | To be documented | Delete a resource |

These rows are documentation placeholders, not claims that the endpoints currently exist.

For each implemented endpoint, document its request parameters, request body, authentication requirements, response format, and possible errors.

---

## Database Configuration

The application uses MongoDB and Mongoose.

Database configuration is organized under:

```text
src/config/db.ts
```

The database connection should use environment variables rather than hardcoded connection strings.

### Recommended Practices

- Keep database credentials private.
- Handle connection failures gracefully.
- Validate data before storing it.
- Define appropriate Mongoose schemas and validation rules.
- Use indexes where beneficial.
- Restrict database network access.
- Use appropriate backups for production data.

---

## Player Module

The player module is located in:

```text
src/modules/player/
```

### Module Files

| File | Responsibility |
|---|---|
| `player.controller.ts` | Handles player-related HTTP requests |
| `player.model.ts` | Defines the player database model |
| `player.routes.ts` | Defines player-related routes |
| `player.service.ts` | Contains player-related business logic |

This separation helps keep player functionality organized and easier to maintain.

Actual player fields, endpoint paths, and available operations should be documented based on the implementation.

---

## Payment Module

The payment module is located in:

```text
src/modules/payment/
```

### Module Files

| File | Responsibility |
|---|---|
| `payment.controller.ts` | Handles payment-related HTTP requests |
| `payment.model.ts` | Defines the payment data model |
| `payment.routes.ts` | Defines payment-related routes |
| `payment.service.ts` | Contains payment-related business logic |
| `payment.types.ts` | Defines payment-related TypeScript types |

Additional Razorpay configuration and helper functions are organized in:

```text
src/config/razorpay.ts
src/shared/utils/razorpay.ts
```

### Payment Security

For a secure payment implementation:

- Create payment orders on the server.
- Keep Razorpay secret keys on the backend.
- Verify payment signatures on the server.
- Verify transaction status before confirming a payment.
- Validate webhook signatures if webhooks are implemented.
- Handle duplicate requests and payment retries safely.
- Never trust a payment-success status supplied only by the frontend.

The presence of payment dependencies does not guarantee that every payment flow has been implemented.

---

## Uploads Module

Upload-related functionality is organized under:

```text
src/modules/uploads/
```

The project includes Multer and Cloudinary dependencies for file uploads and media management.

### Recommended Practices

- Validate permitted file types and sizes.
- Restrict uploads according to the application requirements.
- Keep storage credentials on the server.
- Avoid trusting user-provided filenames.
- Handle upload failures and cleanup appropriately.
- Prevent unauthorized users from uploading or deleting protected media.

The specific upload endpoints and storage behavior depend on the module implementation.

---

## Error Handling

Global error-handling middleware is located in:

```text
src/middlewares/globalErrorHandler.ts
src/middlewares/notFoundHandler.ts
```

Shared error and asynchronous utilities are located in:

```text
src/utils/apiError.ts
src/utils/catchAsynch.ts
src/utils/sendResponse.ts
```

These utilities provide a foundation for consistent error handling and API responses.

### Recommended Practices

- Return suitable HTTP status codes.
- Avoid exposing stack traces in production responses.
- Handle validation and database errors consistently.
- Log server-side errors without logging credentials or sensitive data.
- Return useful, consistent error messages to clients.

---

## Logging and Utilities

The project includes reusable utilities for common backend operations.

| File | Purpose |
|---|---|
| `src/config/logger.ts` | Logging configuration |
| `src/config/dns.ts` | DNS-related configuration or handling |
| `src/utils/apiError.ts` | API error utility |
| `src/utils/catchAsynch.ts` | Asynchronous error-handling helper |
| `src/utils/getRoutes.ts` | Route-related utility |
| `src/utils/methodTag.ts` | HTTP method-related utility |
| `src/utils/pagination.ts` | Pagination helper |
| `src/utils/printBanner.ts` | Terminal banner output |
| `src/utils/sendResponse.ts` | Standardized API response utility |

The exact behavior of each utility is determined by its implementation.

---

## Frontend Integration

**BPL Official Frontend:** https://bpl-official2026.netlify.app/

The frontend can communicate with the backend through HTTP API requests.

### Integration Checklist

1. Deploy the backend to a suitable hosting platform.
2. Configure the backend's environment variables.
3. Set the correct allowed frontend origin in CORS.
4. Configure the frontend to use the deployed backend API URL.
5. Ensure the frontend and backend use compatible request and response formats.
6. Test the API from the deployed frontend.
7. Keep all server-side secrets out of frontend environment variables that are exposed to the browser.

The Netlify URL is the frontend address. It should not be treated as the backend API URL unless the backend is explicitly hosted there as well.

---

## Security Best Practices

- Never commit `.env` files or private credentials.
- Use Helmet with appropriate security settings.
- Configure CORS for trusted origins.
- Validate and sanitize incoming request data.
- Implement authentication and authorization for protected operations.
- Validate uploaded files and enforce request-size limits.
- Verify Razorpay payments server-side.
- Use HTTPS in production.
- Keep dependencies updated.
- Protect database access with appropriate permissions.
- Avoid returning sensitive information in error responses.
- Use secure logging and database backup practices.

### Recommended `.gitignore`

```gitignore
# Dependencies
node_modules/

# Compiled output
dist/

# Environment variables
.env
.env.*
!.env.example

# Logs
*.log
logs/

# Coverage
coverage/

# Operating system
.DS_Store
Thumbs.db

# Editor
.vscode/
.idea/
```

Adjust this file if any of the listed directories or files need to be version-controlled for your deployment workflow.

---

## Build and Deployment

The project can be deployed to a Node.js-compatible hosting platform.

### Production Checklist

1. Install the required dependencies.
2. Configure the production environment variables.
3. Confirm that the MongoDB database is accessible.
4. Run the TypeScript build.
5. Confirm that the compiled entry point exists.
6. Configure the hosting platform to run `npm start`.
7. Configure CORS for the frontend's production origin.
8. Test the API and required integrations.
9. Check server logs and error responses.
10. Confirm that no secrets are committed to the repository.

### Build Command

```bash
npm run build
```

### Start Command

```bash
npm start
```

The configured start command expects the compiled server to be located at:

```text
dist/server.js
```

Ensure the `outDir` and `rootDir` settings in `tsconfig.json` produce this exact path. If the output is instead `dist/src/server.js`, update the TypeScript configuration or start script accordingly.

---

## Troubleshooting

### MongoDB Connection Error

- Check the MongoDB connection string.
- Verify database credentials.
- Check network access and database availability.
- Review the database configuration in `src/config/db.ts`.

### CORS Error

- Verify the frontend origin.
- Check the CORS middleware configuration.
- Confirm that the deployed frontend uses the correct backend URL.

### Build Error

- Run `npm install`.
- Check TypeScript errors.
- Verify `tsconfig.json`.
- Confirm that all imported modules and source files exist.

### Production Server Does Not Start

- Run `npm run build`.
- Confirm that `dist/server.js` exists.
- Verify the configured start script.
- Check whether the hosting platform has the required environment variables.

### Payment Integration Error

- Verify Razorpay configuration.
- Check that the correct test or live credentials are being used.
- Review server-side signature verification.
- Never share secret keys in logs or support requests.

### File Upload Error

- Check upload configuration and permitted file sizes.
- Verify Cloudinary credentials if Cloudinary is used.
- Review server logs for the underlying error.

---

## Future Improvements

Potential improvements for the BPL Backend include:

- Complete match management functionality.
- Expand player management features.
- Add authentication and role-based authorization where required.
- Add request validation schemas.
- Introduce automated unit and integration tests.
- Document API endpoints using OpenAPI or Swagger.
- Add rate limiting and additional abuse protections.
- Improve structured logging and monitoring.
- Add automated deployment workflows.
- Improve payment reconciliation and webhook handling where required.
- Add database indexes and query optimization as usage grows.

These are possible future enhancements, not a statement that they are already implemented.

---

## Contributing

Contributions and improvements are welcome.

1. Fork the repository if it is public, or obtain access if it is private.
2. Create a feature branch.
3. Make focused changes.
4. Test your changes.
5. Write clear commit messages.
6. Submit a pull request when appropriate.

Please avoid committing secrets, generated files, or unrelated changes.

---

## License

No license has been specified in the supplied project information.

Until a license is added, others should not assume that they have permission to copy, distribute, or modify this code. Add an appropriate license if you intend to permit reuse.

---

## Author

**Amol Pawar**

Full Stack Developer | React.js | TypeScript | Node.js

- **GitHub:** https://github.com/amolpawar24
- **BPL Official Frontend:** https://bpl-official2026.netlify.app/
- **Backend Repository:** https://github.com/amolpawar24/BPL-Backend

---

## Acknowledgements

Built as part of the BPL Official application for the **Bhalawani Premier League**.

**BPL Official — Cricket. Community. Competition.**
