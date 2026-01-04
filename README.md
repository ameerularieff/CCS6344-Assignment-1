<h1>CCS6344 – Assignment 1 | TT2L Group 25</h1>

<h2>📘 Subject Registration System</h2>

<p><strong>Technology Stack:</strong> ASP.NET Core (Razor Pages) + Microsoft SQL Server</p>

<p>
This repository contains a secure web-based <strong>Subject Registration System</strong> developed using
ASP.NET Core Razor Pages and Microsoft SQL Server.
The system implements multiple database-level security features including auditing,
row-level security (RLS), data masking, password hashing, password policy enforcement,
and session control.
</p>

<hr>

<h2>🧩 System Requirements</h2>

<p>Before restoring the project, ensure the following are installed:</p>

<ul>
  <li>Microsoft Visual Studio 2022</li>
  <li>ASP.NET and Web Development workload</li>
  <li>Microsoft SQL Server (2019 / 2022)</li>
  <li>SQL Server Management Studio (SSMS)</li>
  <li>.NET SDK 6.0 or later</li>
</ul>

<hr>

<h2>📂 Project Structure Overview</h2>

<pre>
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
</pre>

<hr>

<h2>🗄️ Step 1: Restore the Database (SSMS)</h2>

<ol>
  <li>Open <strong>SQL Server Management Studio (SSMS)</strong></li>
  <li>Connect using <strong>Windows Authentication</strong> or a <strong>sysadmin</strong> account</li>
  <li>Open the scripts inside the <code>Database Queries</code> folder</li>
</ol>

<p><strong>Run the scripts in the following exact sequence:</strong></p>

<ol>
  <li>00_DropDatabase.sql</li>
  <li>01_CreateDatabase.sql</li>
  <li>02_TableCreation.sql</li>
  <li>03_InsertSample.sql</li>
  <li>04_CreateLoginsAndUsers.sql</li>
  <li>05_AssignRolesAndPermissions.sql</li>
  <li>06_CreateRLSFunction.sql</li>
  <li>07_CreateRLSPolicy.sql</li>
  <li>08_CreateAudit.sql</li>
  <li>09_CreateServerAuditSpec.sql</li>
  <li>10_CreateDatabaseAuditSpec.sql</li>
  <li>11_OptResetData.sql</li>
</ol>

<hr>

<h2>🔐 Step 2: Verify Database Security (Optional but Recommended)</h2>

<p>The database includes the following security implementations:</p>

<ul>
  <li>SQL logins: <code>SR_AppUser</code>, <code>SR_DBAdmin</code>, <code>SR_Auditor</code></li>
  <li>Row-Level Security (RLS)</li>
  <li>Server and Database Audit Specifications</li>
  <li>Data masking on sensitive fields</li>
  <li>Password policy enforcement</li>
</ul>

<p>These can be verified in SSMS under:</p>

<ul>
  <li><strong>Security → Logins</strong></li>
  <li><strong>Security → Database Audit Specifications</strong></li>
  <li><strong>Security → Policies</strong></li>
</ul>

<hr>

<h2>🖥️ Step 3: Restore and Run the Web Application (Visual Studio)</h2>

<ol>
  <li>Open <strong>Visual Studio 2022</strong></li>
  <li>Select <strong>Open a project or solution</strong></li>
  <li>Open <code>SubjectRegistrationSystem.slnx</code></li>
  <li>Allow Visual Studio to restore NuGet packages automatically</li>
</ol>

<hr>

<h2>🔗 Step 4: Configure Database Connection</h2>

<p>
Open <code>appsettings.json</code> and ensure the connection string matches your SQL Server instance:
</p>

<pre>
"ConnectionStrings": {
  "DefaultConnection":
  "Server=YOUR_SERVER_NAME;
   Database=SubjectRegistrationDB;
   Trusted_Connection=True;
   TrustServerCertificate=True;"
}
</pre>

<p>
If SQL Authentication is used, replace <code>Trusted_Connection=True</code> with the appropriate
username and password.
</p>

<hr>

<h2>▶️ Step 5: Run the Application</h2>

<ol>
  <li>Press <strong>Ctrl + F5</strong> or click <strong>Run</strong></li>
  <li>The application will launch in your browser</li>
  <li>Login using the sample credentials inserted into the database</li>
</ol>

<hr>

<h2>👥 Sample User Roles</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Role</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Admin</td>
    <td>Manage subjects and view student registrations</td>
  </tr>
  <tr>
    <td>Student</td>
    <td>Register and drop subjects</td>
  </tr>
  <tr>
    <td>Auditor</td>
    <td>Read-only access for audit verification</td>
  </tr>
</table>

<hr>

<h2>🔍 Step 6: Verify Security Features</h2>

<ul>
  <li><strong>Password Hashing:</strong> Passwords are stored as hashes in the <code>Users</code> table</li>
  <li><strong>Password Policy:</strong> Enforced via SQL Server login policies</li>
  <li><strong>Session Expiry:</strong> Users are logged out after inactivity</li>
  <li><strong>Row-Level Security:</strong> Students can only view their own records</li>
  <li><strong>Auditing:</strong> Login and data access activities are recorded</li>
  <li><strong>Data Masking:</strong> Sensitive fields are partially hidden for non-privileged users</li>
</ul>
