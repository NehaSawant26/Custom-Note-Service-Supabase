# 2-Hour Supabase Mini–Project – Custom Note Service

a minimal Supabase backend for a personal “notes” service

## Setup and Deploy

## Installation

Install node packages with npm

```bash
  npm install

```

## Setup Environment Variables

SUPABASE_URL=<your-supabase-url>
SUPABASE_ANON_KEY=<your-anon-key>

## Run Locally

To run this backend Locally

```bash
node server.js

```

## Demo CURL commands

#### For Post '/notes'

# Create a new note

curl -X POST https://<your-project>.functions.supabase.co/post_notes \
 -H "Authorization: Bearer YOUR_JWT_TOKEN" \
 -H "Content-Type: application/json" \
 -d '{"title": "First Note", "content": "This is a test note."}'

#### For Get '/notes'

# Get all notes

curl -X GET https://<your-project>.functions.supabase.co/get_notes \
 -H "Authorization: Bearer YOUR_JWT_TOKEN"

## Schema Design – Why?

#### Schema

```sql
CREATE TABLE notes (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id uuid NOT NULL,
  title text NOT NULL,
  content text,
  created_at timestamp with time zone DEFAULT now()
);
```

- UUID Primary Key: Safer and scalable across distributed systems.
- user_id: Required for user-level data isolation.
- title: Essential identifier for a note.
- content: Optional freeform text.
- created_at: Default timestamp for ordering and audit.

## Endpoints – Why?

- POST /notes: Creates a new note. Parameters come from the request body.

- GET /notes: Fetches all notes. User is identified via the Authorization header.
