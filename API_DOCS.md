# Dreamlytics API Reference

> Comprehensive documentation for all Dreamlytics backend endpoints, request/response formats, authentication, error handling, and usage examples. Updated: 2025-11-18

---

## General Information
- **Base URL:** `/api/`
- **Format:** JSON
- **Authentication:** Most endpoints require JWT token (`Authorization: Bearer <token>`)
- **Error Handling:** All responses include `success`, `error`, and optionally `requestId` fields.

---

## Authentication Endpoints

### `POST /api/auth/login`
Authenticate user and receive JWT token.

**Request Body:**
```json
{
  "emailOrUsername": "user@example.com",
  "password": "yourPassword"
}
```
**Response:**
```json
{
  "success": true,
  "token": "<jwt-token>",
  "user": {
    "id": "...",
    "email": "...",
    "name": "..."
  }
}
```
**Errors:**
- `400`: Invalid input format
- `401`: Invalid credentials

---

### `POST /api/auth/register`
Register a new user.

**Request Body:**
```json
{
  "email": "user@example.com",
  "name": "username",
  "password": "yourPassword"
}
```
**Response:**
```json
{
  "success": true,
  "user": { "id": "...", "email": "...", "name": "..." },
  "token": "<jwt-token>"
}
```

---

### `POST /api/auth/logout`
Logout user (invalidate token).

**Response:**
```json
{
  "success": true
}
```

---

### `GET /api/auth/me`
Get current user profile (requires JWT).

**Response:**
```json
{
  "success": true,
  "user": { "id": "...", "email": "...", "name": "..." }
}
```

---

## Dream Journal Endpoints

### `GET /api/dreams`
List all dreams for the authenticated user.

**Response:**
```json
{
  "success": true,
  "dreams": [
    {
      "id": "...",
      "title": "...",
      "content": "...",
      "date": "2025-11-18",
      "tags": ["..."],
      "isPublic": false,
      "createdAt": "...",
      "updatedAt": "..."
    }
  ]
}
```

---

### `POST /api/dreams`
Create a new dream entry.

**Request Body:**
```json
{
  "title": "Running in the forest",
  "content": "I was running...",
  "date": "2025-11-18",
  "tags": ["forest", "running"],
  "isPublic": false
}
```
**Response:**
```json
{
  "success": true,
  "dream": {
    "id": "...",
    "title": "...",
    "content": "...",
    "date": "...",
    "tags": ["..."],
    "isPublic": false,
    "createdAt": "...",
    "updatedAt": "..."
  }
}
```

---

### `GET /api/dreams/:id`
Get a specific dream by ID.

### `PUT /api/dreams/:id`
Update a dream entry.

### `DELETE /api/dreams/:id`
Delete a dream entry.

### `POST /api/dreams/:id/like`
Like a dream entry.

---

## AI Analysis Endpoints

### `POST /api/analyze`
Analyze a dream using AI models.

**Request Body:**
```json
{
  "dreamContent": "I was flying...",
  "dreamTitle": "Flying dream",
  "tags": ["flying"],
  "dreamId": "...",
  "isRefresh": false
}
```
**Response:**
```json
{
  "success": true,
  "analysis": {
    "motifs": ["flying", "freedom"],
    "emotions": ["joy", "excitement"],
    "summary": "The dream reflects a desire for freedom..."
  }
}
```

---

## Motif & Emotion Extraction

### `POST /api/extract`
Extract motifs and emotions from dream text.

**Request Body:**
```json
{
  "dreamText": "I was flying..."
}
```
**Response:**
```json
{
  "success": true,
  "motifs": ["flying"],
  "emotions": ["joy"]
}
```

---

## Analytics Endpoints

### `GET /api/analytics/emotion-timeline`
Returns emotional timeline for the user.

### `GET /api/analytics/dream-frequency`
Returns dream frequency statistics.

### `GET /api/analytics/motif-frequency`
Returns motif frequency statistics.

---

## Public Feed

### `GET /api/public/dreams`
List public dreams shared by the community.

---

## Admin Endpoints

### `POST /api/admin/cleanup-duplicates`
Remove duplicate dreams.

### `GET /api/admin/fix-indexes`
Fix database indexes.

---

## Mobile Health

### `GET /api/mobile/health`
Check mobile API health status.

---

## Response Format
All endpoints return:
```json
{
  "success": true,
  "data": { ... },
  "error": null,
  "requestId": "..."
}
```
On error:
```json
{
  "success": false,
  "error": "Error message",
  "requestId": "..."
}
```

---

## Authentication
- Private endpoints require JWT token in the `Authorization` header.
- Token is returned after login and must be sent with every request.

---

## Example: Dream Analysis (JavaScript)
```js
fetch('/api/analyze', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer <token>'
  },
  body: JSON.stringify({ dreamContent: 'I was flying...' })
})
  .then(res => res.json())
  .then(data => console.log(data));
```

---

## Versioning
- The API is continuously evolving. Breaking changes are documented here.

---

## Contact & Issue Reporting
- Report bugs or suggestions via GitHub issues.

---

> Last updated: 2025-11-18
