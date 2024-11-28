---
title: Getting Started HRIS
parent: Project
grand_parent: HRIS
layout: default
description: "Getting Started HRIS"
---

# Getting Started

To get started with HRIS, follow these steps:

Clone the repository: `git clone https://github.com/programinglive/hris.git`

```
composer install
npm install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan db:seed
```

Run the application: `php artisan serve`

## How to use HRIS

After running the application, open your web browser and go to `http://localhost:8000`.
You will see the login page.
Use the following credentials to log in:

- Email: `admin@test.com`
- Password: `hrisproject`

After login, you will see the dashboard page.
You can see the list of a menu on the left side.
Click on the menu that you want to access.
For example, if you want to access the employee data, click on the "Employee" menu.

On the employee page, you can see the list of employees.
You can add a new employee by clicking on the "New Employee" button.
You can also edit or delete an existing employee by clicking on the "Edit" or "Delete" button.

You can also access the attendance page by clicking on the "Attendance" menu.
On the attendance page, you can see the list of attendance records.
You can add a new attendance record by clicking on the "New Attendance" button.
You can also edit or delete an existing attendance record by clicking on the "Edit" or "Delete" button.

And so on. You can explore the other menu to see the other features of HRIS.

## Register Company As New User

To register a company as a new user, follow these steps:

1. Click on the "Register Company" button.
2. Fill in the form with the required information.
3. Click on the "Register" button.

After registering, you will be redirected to the login page.

---

<div style="display: flex; flex-direction: column; align-items: center;">
  <a href="https://github.com/programinglive/hris">
    <img src="https://icongr.am/devicon/github-original.svg?size=50&color=currentColor" alt="Github" />
  </a>
  <a href="https://github.com/programinglive/hris">
    Link Repository
  </a>
</div>