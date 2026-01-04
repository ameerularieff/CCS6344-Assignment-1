# CCS6344-Assignment-1
# TT2L Group 25

📘 Subject Registration System

ASP.NET Core + SQL Server

This repository contains a secure web-based Subject Registration System developed using ASP.NET Core Razor Pages and Microsoft SQL Server.
The system includes database-level security features such as auditing, row-level security, data masking, password hashing, and session control.

🧩 System Requirements

Before restoring the project, ensure the following are installed:

Microsoft Visual Studio 2022

ASP.NET and web development workload

Microsoft SQL Server (2019 / 2022)

SQL Server Management Studio (SSMS)

.NET SDK (6.0 or above)

📂 Project Structure Overview
SubjectRegistrationSystem/
│
├── Database Queries/
│   ├── 00_DropDatabase.sql
│   ├── 01_CreateDatabase.sql
│   ├── 02_TableCreation.sql
│   ├── 03_InsertSample.sql
│   ├── 04_OptResetData.sql
│
├── SubjectRegistrationSystem/
│   ├── Pages/
│   ├── Models/
│   ├── Data/
│   ├── Program.cs
│   ├── appsettings.json
│
├── SubjectRegistrationSystem.sln
└── README.md

🗄️ Step 1: Restore the Database (SSMS)

Open SQL Server Management Studio (SSMS)

Connect using Windows Authentication or sysadmin account

Open the Database Queries folder scripts in order:

Run scripts in this exact sequence:
00_DropDatabase.sql        -- (Optional) Clean previous database
01_CreateDatabase.sql     -- Create SubjectRegistrationDB
02_TableCreation.sql      -- Create tables and constraints
03_InsertSample.sql       -- Insert sample users, students, subjects
04_OptResetData.sql       -- Optional reset script


Verify database creation:

USE SubjectRegistrationDB;
SELECT * FROM Users;
SELECT * FROM Subjects;

🔐 Step 2: Verify Database Security (Optional but Recommended)

The database includes:

SQL logins (SR_AppUser, SR_DBAdmin, SR_Auditor)

Row-Level Security (RLS)

Database Audit Specifications

Data masking on sensitive fields

Password policies

You may verify using:

Security → Logins

Security → Database Audit Specifications

Security → Policies

🖥️ Step 3: Restore and Run the Web Application (Visual Studio)

Open Visual Studio

Select Open a project or solution

Open:

SubjectRegistrationSystem.sln


Restore dependencies:

Visual Studio will automatically restore NuGet packages

🔗 Step 4: Configure Database Connection

Open appsettings.json and ensure the connection string matches your SQL Server instance:

"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER_NAME;Database=SubjectRegistrationDB;Trusted_Connection=True;TrustServerCertificate=True;"
}


If using SQL Authentication, replace Trusted_Connection=True with username and password.

▶️ Step 5: Run the Application

Press Ctrl + F5 or click Run

The application will launch in your browser

Login using sample credentials inserted in the database

👥 Sample User Roles
Role	Description
Admin	Manage subjects and view student registrations
Student	Register and drop subjects
Auditor	Read-only access for audit verification
🔍 Step 6: Verify Security Features

Password Hashing: View hashed passwords in Users table

Session Expiry: User is logged out after inactivity

Row-Level Security: Students only see their own records

Auditing: Login and data actions recorded in audit logs

Data Masking: Sensitive fields partially hidden for non-privileged users

✅ Notes for Evaluators

Database scripts are provided for full restoration

Security controls are implemented at database level

Application uses parameterized queries to prevent SQL Injection

Auditing and RLS are verifiable directly in SSMS
