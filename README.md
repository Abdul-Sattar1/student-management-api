# Student Management API

A CRUD REST API for managing student records, built for the Software Quality Engineering (SW426) PBL at MUET SZAB Campus, Khairpur Mir's, by Abdul Sattar (K22SW012).

## Features

- Create, read (all and by ID), update and delete students
- JSON request and response bodies
- Mongoose schema validation
- Proper HTTP status codes (201, 200, 400, 404, 500)
- Duplicate roll number check
- Invalid ID and malformed JSON handling

## Tech Stack

- Node.js
- Express.js
- MongoDB Atlas
- Mongoose
- dotenv
- Nodemon
- Postman

## Student Fields

| Field        | Type   | Rules                               |
| ------------ | ------ | ----------------------------------- |
| `name`       | String | Required                            |
| `rollNo`     | String | Required, unique                    |
| `department` | String | Required                            |
| `age`        | Number | Required, whole number from 1 to 120 |
| `semester`   | Number | Required, whole number from 1 to 12  |
| `_id`        | ObjectId | Added automatically               |
| `createdAt`  | Date   | Added automatically                 |
| `updatedAt`  | Date   | Added automatically                 |

## Project Structure

```
student-management-api/
├── models/
│   └── Student.js
├── routes/
│   └── students.js
├── .env.example
├── .gitignore
├── package.json
├── README.md
└── server.js
```

## Getting Started

### Prerequisites

- Node.js
- MongoDB Atlas account or a local MongoDB installation

### Installation

1. Install the dependencies:

   ```bash
   npm install
   ```

2. Copy `.env.example` to `.env` and fill in your values:

   ```bash
   cp .env.example .env
   ```

   ```
   PORT=3000
   MONGODB_URI=your_mongodb_connection_string_here
   ```

3. Start the server in development mode:

   ```bash
   npm run dev
   ```

The server runs at http://localhost:3000.

## API Endpoints

Base URL: `http://localhost:3000/api/students`

| Method | Endpoint            | Description          | Status Codes  |
| ------ | ------------------- | -------------------- | ------------- |
| POST   | `/api/students`     | Create a student     | 201           |
| GET    | `/api/students`     | Get all students     | 200           |
| GET    | `/api/students/:id` | Get a student by ID  | 200, 400, 404 |
| PUT    | `/api/students/:id` | Update a student     | 200, 400, 404 |
| DELETE | `/api/students/:id` | Delete a student     | 200, 400, 404 |

### Example POST Request Body

```json
{
  "name": "Abdul Sattar",
  "rollNo": "K22SW012",
  "department": "Software Engineering",
  "age": 22,
  "semester": 7
}
```

### Example Error Responses

400 Bad Request (duplicate roll number):

```json
{ "message": "Roll number already exists" }
```

400 Bad Request (invalid ID):

```json
{ "message": "Invalid student ID" }
```

404 Not Found:

```json
{ "message": "Student not found" }
```

## Testing

The API was tested with Postman. The test cases covered:

- Valid CRUD requests
- Missing and invalid fields
- Duplicate roll number
- Invalid and nonexistent IDs
- Deleted record returns 404
- Malformed JSON
- Unknown route

## Author

Abdul Sattar (K22SW012)
Department of Software Engineering
MUET SZAB Campus, Khairpur Mir's
