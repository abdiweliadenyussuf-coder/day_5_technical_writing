# DAY 5 ASSIGNMENT: TECHNICAL WRITING

# A) USER MANUAL PROCEDURE

## Task: Setting Up a GitHub Repository and Making the First Commit

### 1. Introduction

This procedure explains how to create a GitHub repository and make the first commit. GitHub is an online platform used to store, manage, and share code projects. This guide is designed for beginners with basic computer knowledge.

### 2. Prerequisites

Before starting, the user needs:

- A computer with internet access.
- A web browser such as Google Chrome.
- A GitHub account.
- A valid email address.
- Basic computer knowledge.

### 3. Step-by-Step Procedure

**Step 1: Open GitHub**

Action: Open your web browser and visit https://github.com.

Expected result: The GitHub homepage appears.

**Step 2: Sign in to your account**

Action: Enter your GitHub username and password and click Sign in.

Expected result: Your GitHub dashboard opens.

**Step 3: Start creating a repository**

Action: Click the plus (+) icon at the top-right corner and select New repository.

Expected result: The repository creation page appears.

**Step 4: Enter the repository name**

Action: Type a name for your repository in the Repository name field.

Expected result: The repository name appears in the field.

**Step 5: Choose repository visibility**

Action: Select Public as the repository visibility.

Expected result: The Public option is selected.

**Step 6: Create the repository**

Action: Click the Create repository button.

Expected result: A new, empty repository is created.

**Step 7: Create a README file**

Action: Click Add file and select Create new file.

Expected result: A new file editing page appears.

**Step 8: Name the file**

Action: Enter README.md as the filename.

Expected result: The filename appears in the file name field.

**Step 9: Add project information**

Action: Write a short description of your project in the editing area.

Expected result: The project information appears in the README editor.

**Step 10: Make the first commit**

Action: Click Commit changes.

Expected result: The README.md file is saved in the repository, and the first commit is created.

### 4. Screenshot Description

The screenshot should show the GitHub repository page after the first commit. It should clearly display the repository name, the README.md file, and the commit information.

### 5. Troubleshooting

**Common problem: Repository is empty.**

This error occurs when a repository has been created without adding or committing any files.

**Solution:** Create a README.md file, add some project information, and click Commit changes. Refresh the repository page to confirm that the file is available.

### 6. Conclusion

Following these steps helps beginners create a GitHub repository and make their first commit. It also provides basic experience in using GitHub to manage and store project files.

---

# B) API REFERENCE ENTRY

## API Name: Create a New Task

### 1. Overview

The Create Task API allows an authenticated user to create a new task within a project management application. The user provides the task title, description, assignee, due date, and priority level.

### 2. HTTP Method and Endpoint

**HTTP Method:** POST

**Endpoint:**

`/api/v1/projects/{projectId}/tasks`

**Description:** Creates a new task inside a specified project.

### 3. Request Parameters

#### A. Path Parameters

| Parameter | Data Type | Required | Description |
|---|---|---|---|
| projectId | String (UUID) | Yes | Unique ID of the project where the task will be created. |

#### B. Query Parameters

No query parameters are required for this endpoint.

#### C. Request Body Parameters

| Parameter | Data Type | Required | Description |
|---|---|---|---|
| title | String | Yes | Name or title of the task. |
| description | String | No | Additional information about the task. |
| assigneeId | String (UUID) | Yes | ID of the user assigned to the task. |
| dueDate | String (ISO 8601 date: YYYY-MM-DD) | Yes | Date when the task should be completed. Example: 2026-12-15. |
| priority | String | Yes | Priority level: low, medium, or high. |

### 4. Required Request Headers

| Header | Value | Description |
|---|---|---|
| Authorization | Bearer token | Authenticates the user making the request. |
| Content-Type | application/json | Indicates that the request body is in JSON format. |
| Accept | application/json | Requests a JSON response from the server. |

### 5. Example Request Body

```json
{
  "title": "Complete project documentation",
  "description": "Prepare and review the project documentation.",
  "assigneeId": "550e8400-e29b-41d4-a716-446655440001",
  "dueDate": "2026-12-15",
  "priority": "high"
}
```

### 6. HTTP Response Codes

| Status Code | Meaning | Description |
|---|---|---|
| 201 | Created | The task has been successfully created. |
| 400 | Bad Request | The request contains invalid or missing information. |
| 401 | Unauthorized | The user has not provided valid authentication credentials. |
| 403 | Forbidden | The authenticated user does not have permission to create tasks in the project. |
| 404 | Not Found | The specified project or assignee does not exist. |
| 415 | Unsupported Media Type | The request does not use the supported JSON content type. |
| 500 | Internal Server Error | An unexpected server error occurred while processing the request. |

### 7. Example Successful Response

**Status Code:** 201 Created

```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "taskId": "660e8400-e29b-41d4-a716-446655440002",
    "projectId": "750e8400-e29b-41d4-a716-446655440003",
    "title": "Complete project documentation",
    "description": "Prepare and review the project documentation.",
    "assigneeId": "550e8400-e29b-41d4-a716-446655440001",
    "dueDate": "2026-12-15",
    "priority": "high",
    "status": "pending",
    "createdAt": "2026-11-25T16:30:00Z"
  }
}
```

### 8. Example Error Response

**Status Code:** 400 Bad Request

This response occurs when the request contains missing or invalid information.

```json
{
  "success": false,
  "message": "Invalid request data",
  "errors": [
    {
      "field": "title",
      "message": "Task title is required."
    },
    {
      "field": "priority",
      "message": "Priority must be low, medium, or high."
    }
  ]
}
```

### 9. Conclusion

The Create Task API provides a simple way for authenticated users to add tasks to projects. It accepts task information in JSON format and returns a response indicating whether the task was created successfully. The API also uses HTTP status codes to communicate errors and successful operations.
