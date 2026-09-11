# Unified HR Service Delivery Platform

## 📌 Project Overview

The **Unified HR Service Delivery Platform** is a ServiceNow-based Human Resources Service Delivery solution designed to simplify and automate common HR processes for **Faculty & Staff** within a university environment.

The platform provides a centralized interface where employees can submit HR requests, apply for leave, access HR information, and track their requests. It also provides role-based workflows for **Head of Department (HOD), HR Officers, and HR Administrators** to review, process, and manage requests.

The solution aims to reduce manual HR processes, improve transparency, automate request routing, and provide a better experience for employees and HR teams.

---

## 🎯 Problem Statement

Traditional HR processes in an organization or university can involve:

* Manual leave-request processing
* Multiple communication channels for HR queries
* Difficulty tracking request status
* Delays in approvals
* Lack of centralized HR information
* Repetitive work for HR personnel
* Limited visibility into the progress of requests

The **Unified HR Service Delivery Platform** addresses these challenges by bringing HR services into a single ServiceNow application.

---

## 💡 Proposed Solution

The platform provides a centralized HR service portal with automated workflows for handling employee requests.

Faculty & Staff can:

* Apply for leave
* Raise HR cases
* Track submitted requests
* Access HR policies and information
* Interact with the HR support system

Requests are automatically routed to the appropriate approver based on the user's role and department.

---

## 🚀 Key Features

### 👤 Employee Services

Employees can access HR services through a centralized interface.

Main services include:

* Leave Application
* HR Case Submission
* My Requests
* HR Policies
* Employee Documents
* Announcements

### 📝 Leave Management

Employees can submit leave requests through the platform.

The system maintains information such as:

* Raised By
* Leave Type
* Applied On
* Leave Days
* Current Approver
* Status
* HOD Remarks
* HR Remarks

The leave approval process is automated according to the user's role.

### 🔄 Automated Leave Approval Workflow

The platform uses ServiceNow workflow automation to route leave requests to the appropriate authority.

#### Employee Leave

```text
Employee
   ↓
Department HOD
   ↓
HR Officer
   ↓
Approved / Rejected
```

#### HOD Leave

```text
HOD
 ↓
HR Officer
 ↓
Approved / Rejected
```

#### HR Leave

```text
HR Officer
 ↓
HR Administrator
 ↓
Approved / Rejected
```

This role-based routing ensures that requests are handled by the appropriate authority.

---

## 🏢 Department-Based Approval

The system supports department-specific HOD routing.

For example:

```text
CSE Employee
     ↓
CSE HOD

AI Employee
     ↓
AI HOD
```

This allows leave requests to be routed according to the employee's department.

---

## 🎫 HR Case Management

Faculty & Staff can raise HR cases for HR-related issues or queries.

HR cases can contain information such as:

* Case Number
* Requested By
* Category
* Priority
* Description
* Assigned To
* Status
* Resolution information

HR personnel can process and resolve cases through the ServiceNow platform.

---

## 🔐 Role-Based Access

The application uses role-based access to control what different users can access and perform.

Example roles include:

| Role     | Responsibility                                    |
| -------- | ------------------------------------------------- |
| Employee | Submit and track HR requests                      |
| HOD      | Review department employee requests               |
| HR       | Process HR requests and cases                     |
| HR Admin | Handle administrative approvals and HR management |

---

## 🤖 HR Virtual Assistant

The platform can provide conversational assistance for common HR activities.

The Virtual Assistant can be used to help users:

* Find HR information
* Search HR policies
* Get assistance with HR services
* Initiate HR-related activities

---

## 📚 Knowledge-Based HR Information

HR information can be organized through a centralized knowledge base.

Users can access relevant information such as:

* HR Policies
* Leave-related information
* Frequently asked HR questions
* Employee guidelines

---

## 🔔 Notifications

ServiceNow automation can be used to notify relevant users when important actions occur.

Examples include:

* Leave request submission
* Approval or rejection
* HR case updates
* Request resolution

---

# 🛠️ Setup Instructions

## Prerequisites

Before setting up the application, make sure you have:

* A ServiceNow Personal Developer Instance (PDI) or suitable ServiceNow instance
* `admin` access to the instance
* Access to the application's GitHub repository
* Access to the ServiceNow Studio / App Engine Studio
* GitHub credentials with appropriate repository permissions

---

## 1. Clone or Import the Application

The application is maintained in the GitHub repository:

**Unified-HR-Service-Delivery-Platform**

The ServiceNow application is maintained on the ServiceNow source-control branch:

```text
sn_instances/dlt-hck-8017-0024
```

### Import through ServiceNow Studio

1. Log in to your ServiceNow PDI.
2. Open **App Engine Studio** or **ServiceNow Studio**.
3. Select **Import Application** / **Import app**.
4. Choose **Source Control** as the import source.
5. Select **HTTPS** as the network protocol.
6. Enter the GitHub repository URL.
7. Enter the ServiceNow application branch.
8. Configure the GitHub credential.
9. Start the import.
10. Select the imported application after the import completes.

Example:

```text
Repository:
https://github.com/MalluriKiran/Unified-HR-Service-Delivery-Platform

Branch:
sn_instances/dlt-hck-8017-0024
```

> **Note:** The exact menu names can vary depending on the ServiceNow release and development experience available in the instance.

---

## 2. Configure Application Users

After importing the application, create or configure the required users.

The application uses role-based access for different types of users.

Configure users for:

```text
Employee
HOD
HR
HR Admin
```

Assign the appropriate application roles to each user.

Example:

```text
Employee
   ↓
Employee role

HOD
   ↓
HOD role

HR Officer
   ↓
HR role

HR Administrator
   ↓
Admin role
```

---

## 3. Configure Departments

Create the required departments in the application.

Example departments:

* CSE
* AI
* ME
* CE
* EEE
* Human Resources

Assign the appropriate HOD to each department.

For example:

```text
Department: CSE
HOD: CSE HOD

Department: AI
HOD: AI HOD
```

This department information is used during leave-request routing.

---

## 4. Configure Leave Management

Create/configure the required leave-related data.

The leave request should contain the required information, including:

* Raised By
* Leave Type
* Applied On
* Leave Days
* Current Approver
* Status
* HOD Remarks
* HR Remarks

Configure the default leave balance according to the organization's requirements.

---

## 5. Configure HR Cases

Configure the HR Case functionality and required categories.

Example HR case categories can include:

* Payroll
* Benefits
* Employee Relations
* General HR Queries

Configure the corresponding assignment groups and HR users.

---

## 6. Configure Flow Designer

After the application components are available, verify the application's Flow Designer automations.

The major automation areas include:

### Leave Approval

```text
Leave Request Created
        ↓
Determine Requester's Role
        ↓
Determine Department
        ↓
Find Appropriate Approver
        ↓
HOD / HR / Admin Approval
        ↓
Update Request Status
        ↓
Send Notification
```

### HR Case Processing

```text
HR Case Created
       ↓
Determine Category / Priority
       ↓
Route to Appropriate HR Group
       ↓
HR Processing
       ↓
Resolve Case
       ↓
Notify Employee
```

Make sure the required flows are **active** before testing the application.

---

# 🧪 Demo Instructions

The following demo flow can be used to demonstrate the complete application.

## Demo 1 — Employee Login

1. Log in as an **Employee**.
2. Open the Employee Center.
3. Verify that the HR services are available.
4. Demonstrate the available services such as:

   * Apply Leave
   * Raise HR Case
   * My Requests
   * HR Policies
   * Employee Documents
   * Announcements

---

## Demo 2 — Apply for Leave

1. Open **Apply Leave**.
2. Select the required leave type.
3. Enter the required dates/details.
4. Submit the request.
5. Verify that the request is created.
6. Open **My Requests**.
7. Show the submitted request and its status.

The system should automatically determine the appropriate approval path.

---

## Demo 3 — HOD Approval

1. Log in or impersonate the relevant **HOD**.
2. Open the requests assigned to the HOD.
3. Open the employee's leave request.
4. Review the request.
5. Enter HOD remarks if required.
6. Approve or reject the request.

If approved, the request proceeds to the next stage of the workflow.

---

## Demo 4 — HR Processing

1. Log in as an **HR Officer**.
2. Open the request routed to HR.
3. Review the leave request.
4. Add HR remarks if required.
5. Approve or reject the request.
6. Verify that the request status is updated.

---

## Demo 5 — HR Admin Approval

For HR-related requests requiring administrative approval:

1. Log in as **HR Admin**.
2. Open the request.
3. Review the request and previous approvals.
4. Approve or reject the request.
5. Verify the final status.

---

## Demo 6 — Raise an HR Case

1. Log in as an Employee.
2. Select **Raise HR Case**.
3. Enter the HR issue/query.
4. Select the appropriate category.
5. Submit the case.
6. Verify that the HR Case number is generated.
7. Open **My Requests** and verify the case status.

---

## Demo 7 — HR Case Routing

1. Log in as an HR user.
2. Open the newly created HR case.
3. Verify the assigned HR group/user.
4. Process the case.
5. Update the case status.
6. Resolve the case.
7. Verify that the employee receives the appropriate notification.

---

## Demo 8 — HR Virtual Assistant

1. Open the Virtual Assistant.
2. Ask an HR-related question.
3. Search for an HR policy or knowledge article.
4. Demonstrate the chatbot's response.
5. If configured, demonstrate initiating an HR service through the Virtual Assistant.

---

## Demo 9 — Role-Based Access

Demonstrate the application using different user roles.

```text
Employee
   ↓
Submit and track requests

HOD
   ↓
Review department requests

HR
   ↓
Process HR cases and requests

HR Admin
   ↓
Administrative approval
```

This demonstrates that users receive access according to their responsibilities.

---

# 🔄 Complete Demo Scenario

For a short hackathon demonstration, the recommended sequence is:

```text
Employee
   │
   ├── Login
   │
   ├── Apply Leave
   │
   ▼
Leave Request Created
   │
   ▼
Department HOD
   │
   ├── Review
   ├── Add Remarks
   └── Approve
   │
   ▼
HR Officer
   │
   ├── Review
   └── Approve
   │
   ▼
Request Completed
   │
   ▼
Employee Notification
```

Then demonstrate:

```text
Employee
   ↓
Raise HR Case
   ↓
Automatic Routing
   ↓
HR Team
   ↓
Case Resolution
   ↓
Employee Notification
```

This gives the reviewer a complete view of both the **Leave Management** and **HR Case Management** capabilities.

---

# 🧰 Technologies Used

* **ServiceNow**
* **ServiceNow App Engine Studio**
* **ServiceNow Studio**
* **Flow Designer**
* **Employee Center**
* **Virtual Agent**
* **Knowledge Management**
* **ServiceNow Tables**
* **Business Rules**
* **Client Scripts**
* **UI Policies**
* **Access Controls (ACLs)**
* **GitHub / Source Control**

---

# 🏗️ Application Architecture

```text
                    ┌──────────────────────┐
                    │      Faculty/Staff   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Employee Center   │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
        Leave Request       HR Case       HR Information
              │                │                │
              ▼                ▼                ▼
        Flow Designer      HR Workflow     Knowledge Base
              │                │
              ▼                ▼
             HOD              HR
              │                │
              └────────┬───────┘
                       ▼
                 HR Administrator
```

---

# 🌟 Benefits

* Centralized HR services
* Reduced manual processing
* Faster request handling
* Automated approval routing
* Better request visibility
* Role-based access control
* Improved communication
* Self-service HR information
* Reduced HR workload
* Better employee experience

---

# 🔮 Future Enhancements

Possible future enhancements include:

* Advanced HR analytics and dashboards
* Mobile HR application
* AI-powered HR assistance
* Automated document generation
* Advanced employee sentiment analysis
* SLA monitoring and escalation
* Integration with university ERP systems
* Attendance and payroll integration
* Advanced HR reporting

---

# 👥 Team NEXORA

This project was developed by **Team NEXORA** as part of the **ServiceNow HackNow Hackathon in collaboration with Deloitte**.

### Team Members

* Nakka Sri Charitha
* Nakka Vyshnavi
* Malluri Naga Kiran
* Metla Likith Kumar Reddy
* Machha Karthik
* Mekala Sai Charan

---

# 📄 Project Information

| Property         | Details                                |
| ---------------- | -------------------------------------- |
| **Project Name** | Unified HR Service Delivery Platform   |
| **Platform**     | ServiceNow                             |
| **Hackathon**    | HackNow in collaboration with Deloitte |
| **Team**         | NEXORA                                 |
| **Repository**   | Unified-HR-Service-Delivery-Platform   |

---

# 📌 Conclusion

The **Unified HR Service Delivery Platform** demonstrates how ServiceNow can be used to build a centralized and automated HR service environment for a university.

By combining employee self-service, automated workflows, role-based approvals, HR case management, knowledge management, and conversational assistance, the platform provides a scalable foundation for modernizing HR service delivery.
