
------------------------------------------------- TA MANAGEMENT SYSTEM -----------------------------------------------------

A Teaching Assistant (TA) management system built with Oracle APEX, developed as a university project.

Overview:
This application helps manage TA-related workflows through a web-based interface built on Oracle APEX and an 
Oracle Database backend.

Tech Stack:
Oracle APEX — low-code application platform (front end, pages, forms, reports)

Oracle Database (PL/SQL / SQL) — data storage and business logic

Authentication:
The app uses a custom authentication scheme instead of default Oracle APEX (workspace) accounts. Login credentials 
are stored in a dedicated TA_USERS table with hashed passwords, validated through a standalone TA_AUTHENTICATE PL/SQL 
function. This keeps login scoped to the application itself, separate from the Oracle APEX workspace.

Project Structure:

TA-Management-System/
│
├── README.md
│
├── apex/
│   └── f133996.sql
│
└── database/
    ├── ta_management-ddl.sql
	
	
Setup / Import Instructions:

Import the app — In Oracle APEX App Builder, go to Import, and upload the contents of the app/ folder (APEXlang format).

Create the schema — Run db/schema.sql against your target Oracle Database schema to create the required tables (TA_USERS) and functions (TA_AUTHENTICATE).

Set the authentication scheme — In the imported app, go to Shared Components > Authentication Schemes, and set the custom scheme as Current.

Create a login — Insert an initial user into TA_USERS (see example below) to be able to log in.

INSERT INTO ta_users (username, password_hash, full_name, role)
VALUES (
    'your_email@.com',
    STANDARD_HASH('your_password', 'SHA256'),
    'Your Name',
    'Admin'
);
COMMIT;

Notes:
No real credentials or student data are stored in this repository — sample/placeholder values only.

Passwords are hashed with STANDARD_HASH (SHA-256) before storage.

Author:
Leo Pathan
East West University,
Bangladesh

