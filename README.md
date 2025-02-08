Dropbox Sign Backend Service

This is the backend service built with NestJS, which integrates with Dropbox Sign (HelloSign) API to enable document signing workflows. It provides endpoints to create document instances, track field data, and facilitate an embedded signing experience.
Features

    Document Creation: Dynamically generate signing requests based on a Dropbox Sign template.
    Field Mapping: Automatically handle and populate dynamic fields within a document.
    Embedded Signing: Enables users to sign documents within the frontend application.
    Webhook Support: Handles updates about document signing status from Dropbox Sign.

Tech Stack

    NestJS: Backend framework.
    Prisma: ORM for database interactions.
    PostgreSQL: Database for storing documents, signers, and field data.
    Dropbox Sign API: External API integration.
    Axios: HTTP client for making API requests.

Installation

    Clone the repository:

git clone https://github.com/Kgabo71/Drobox-sign-BackEnd
cd Drobox-sign-BackEnd

Install dependencies:

npm install

Set up the .env file: Create a .env file in the root directory and add the following:

DATABASE_URL=postgresql://<username>:<password>@<host>:<port>/<database>
DROPBOX_SIGN_API_KEY=<your_dropbox_sign_api_key>
FRONTEND_URL=http://localhost:3000

Generate the Prisma client:

npx prisma generate

Run database migrations:

    npx prisma migrate dev --name init

Usage

    Start the development server:

    npm run start:dev

    The backend service will run at http://localhost:3000.

    API Endpoints:
        POST /documents/create: Create a document instance and return an embedded signing URL.
        POST /webhooks/dropbox-sign: Handles webhooks from Dropbox Sign.

Folder Structure

src/
├── prisma/
│   └── schema.prisma  # Prisma schema for the database
├── documents/
│   ├── documents.controller.ts  # Handles document-related API requests
│   ├── documents.service.ts     # Contains business logic for document creation
│   └── dto/                     # DTOs for validation
├── dropbox-sign/
│   ├── dropbox-sign.controller.ts  # Handles Dropbox Sign-specific API requests
│   ├── dropbox-sign.service.ts     # Integrates with Dropbox Sign API
├── app.module.ts               # Main application module
├── main.ts                     # Application entry point

Key Commands

    Run the app in development mode:

npm run start:dev

Run Prisma Studio to view and manage the database:

npx prisma studio

Build the app:

    npm run build

Deployment

    Ensure you have the environment variables set in the deployment environment.
    Use a production database and run the migrations:

npx prisma migrate deploy

Build and run the application:

    npm run build
    npm run start:prod

License

This project is licensed under the MIT License. See the LICENSE file for details.
