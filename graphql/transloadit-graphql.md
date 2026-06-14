# Transloadit GraphQL Schema

This document describes a conceptual GraphQL schema for the Transloadit file uploading and media processing API. Transloadit provides a REST API for creating and managing Assemblies (processing jobs), Templates, Template Credentials, Webhooks, Billing, and Queue monitoring, supporting 94 Robots for automation of video encoding, image manipulation, audio processing, document conversion, and AI-based media tasks.

## Schema Source

Derived from the Transloadit REST API documentation at https://transloadit.com/docs/api/

## Core Concepts

### Assemblies

An Assembly is the central processing unit in Transloadit. Each Assembly represents a single processing job that takes uploaded files as input and applies a series of Steps (defined by Robots) to produce output files. Assemblies have a lifecycle: created, uploading, executing, completed, or errored.

### Robots

Robots are the individual processing steps within an Assembly. Transloadit provides 94 Robots covering tasks such as video encoding, image resizing, audio extraction, thumbnail generation, file format conversion, speech transcription, and storage integrations with services like S3 and Google Drive.

### Templates

Templates allow pre-defining Assembly Instructions so they can be reused without passing the full instruction set on every API call. Templates support dynamic variables to allow customization at runtime.

### Uploads

Files are uploaded into an Assembly either via multipart form POST (browser or server-side), resumable uploads (Tus protocol via Uppy), or by referencing remote URLs. Each uploaded file is tracked with metadata including name, size, MIME type, and URL.

### Notifications

Transloadit sends webhook notifications to a configured URL when an Assembly completes or errors, allowing asynchronous processing workflows.

## Types Overview

- **Assembly types**: Assembly, AssemblyDetails, AssemblyStatus, AssemblyNotifications, AssemblyResults
- **File types**: File, FileDetails, FileID, FileName, FileSize, FileMime, FileURL, OriginalFile
- **Step types**: Step, StepDetails, StepResult
- **Robot types**: Robot, RobotDetails, RobotType
- **Instruction types**: Instructions, InstructionsDetails
- **Template types**: Template, TemplateDetails, TemplateName, TemplateContent
- **Notification types**: Notification, NotificationDetails, NotificationURL, NotificationStatus, NotificationSign
- **Upload types**: Upload, UploadDetails, UploadFile, UploadMultipart
- **Best practice types**: BestPractice
- **Queue types**: Queue, QueueDetails, QueueStatus
- **Account types**: Account, AccountDetails
- **Billing types**: Bill, BillDetails, BillItem
- **Subscription types**: Subscription, SubscriptionDetails, SubscriptionPlan
- **Payment types**: CreditCard
- **Auth types**: APIKey, AuthKey, AuthSecret
- **Webhook types**: WebhookEvent
- **Signature types**: Signature, SignatureType
- **Error types**: Error, ErrorDetails

## Queries

- `assembly(id: ID!)`: Fetch a single Assembly by ID
- `assemblies(status: AssemblyStatus, limit: Int, offset: Int)`: List Assemblies
- `template(id: ID!)`: Fetch a single Template by ID
- `templates(limit: Int, offset: Int)`: List Templates
- `queue`: Fetch current Queue status
- `account`: Fetch Account details
- `bill(month: String!)`: Fetch billing information for a given month
- `notifications(assemblyId: ID!)`: Fetch notifications for an Assembly

## Mutations

- `createAssembly(input: AssemblyInput!)`: Create and start a new Assembly
- `cancelAssembly(id: ID!)`: Cancel a running Assembly
- `replayAssembly(id: ID!)`: Replay a completed Assembly
- `createTemplate(input: TemplateInput!)`: Create a new Template
- `updateTemplate(id: ID!, input: TemplateInput!)`: Update an existing Template
- `deleteTemplate(id: ID!)`: Delete a Template

## Subscriptions

- `assemblyStatusChanged(id: ID!)`: Stream Assembly status updates in real time
