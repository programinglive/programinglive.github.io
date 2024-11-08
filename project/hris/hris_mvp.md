---
title: MVP (HRIS)
parent: HRIS
nav_order: 1
description: "Human Resource Information System MVP"
---

# MVP
Human Resource Information System MVP is a web application designed to support the management of human resources in a company. HRIS MVP will make it easier for companies to manage their employees, including managing employee data, managing attendance, managing salary, and managing employee training.

## Initial Setup

- A new user can register a company

```mermaid
sequenceDiagram
    actor User
    participant Browser
    participant Server

    User->>Browser: Clicks "Register Company" link
    activate Browser
    Browser->>Server: GET /register_company
    activate Server
    Server-->>Browser: Registration form
    deactivate Server
    Browser->>User: Displays registration form
    deactivate Browser

    User->>Browser: Inputs company name
    activate Browser
    User->>Browser: Inputs company address
    User->>Browser: Inputs company phone
    Browser->>Server: POST /register_company with data
    activate Server
    Server-->>Server: Validates data
    alt Valid data
        Server-->>Server: Creates company record
        Server-->>Browser: Success message
        Browser->>User: Displays success message
    else Invalid data
        Server-->>Browser: Error message
        Browser->>User: Displays error message
    end
    deactivate Server
    deactivate Browser
```

- A new user can create a user admin. 

---
<div style="display: flex; flex-direction: column; align-items: center;">
  <a href="https://github.com/programinglive/hris">
    <img src="https://icongr.am/devicon/github-original.svg?size=50&color=currentColor" alt="Github" />
  </a>
  <a href="https://github.com/programinglive/hris">
    Link Repository
  </a>
</div>