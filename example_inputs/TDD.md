## **Technical Design Document: Personal Task Manager**

### **1\. Introduction**

This document details the technical design for the Personal Task Manager web application, as described in the accompanying Product Requirements Document (PRD). The application will be built using the Flask micro-framework and will leverage a lightweight database for data persistence.

### **2\. Architecture Overview**

The application will follow a classic Model-View-Controller (MVC) pattern (though Flask is more flexible, we'll align with this mental model):

* **Model:** SQLite database for data storage, managed via SQLAlchemy ORM.  
* **View:** HTML templates rendered using Jinja2.  
* **Controller:** Flask routes handling requests, interacting with the model, and rendering views.

### **3\. Database Design**

A single table, Task, will be used to store task information.

* **Table Name:** tasks  
* **Fields:**  
  * id (INTEGER, PRIMARY KEY, AUTOINCREMENT): Unique identifier for each task.  
  * title (TEXT, NOT NULL): The description of the task.  
  * completed (BOOLEAN, DEFAULT FALSE): Status of the task (true if completed, false otherwise).  
  * created\_at (DATETIME, DEFAULT CURRENT\_TIMESTAMP): Timestamp when the task was created.

### **4\. API Endpoints (Flask Routes)**

* **/ (GET):**  
  * **Purpose:** Display all tasks (both active and completed).  
  * **Logic:** Fetch all tasks from the tasks table, order by created\_at (descending). Render index.html.  
* **/add (POST):**  
  * **Purpose:** Add a new task.  
  * **Logic:** Receive task title from form data. Create a new Task record in the database. Redirect to /.  
* **/complete/\<int:task\_id\> (GET):**  
  * **Purpose:** Mark a task as completed.  
  * **Logic:** Retrieve Task by task\_id. Update its completed field to True. Redirect to /.  
* **/delete/\<int:task\_id\> (GET):**  
  * **Purpose:** Delete a task.  
  * **Logic:** Retrieve Task by task\_id. Delete the record from the database. Redirect to /.

### **5\. Component Design**

* **app.py:** Main Flask application file. Initializes the app, database, and defines routes.  
* **models.py:** Defines the SQLAlchemy Task model.  
* **templates/index.html:** The main HTML template for displaying tasks and the input form. Will include basic styling.  
* **static/css/style.css:** For custom CSS to improve aesthetics.

### **6\. Technical Challenges / Considerations**

* **Error Handling:** Implement basic error handling for database operations (e.g., task not found).  
* **Input Validation:** Basic validation for task title (e.g., not empty).  
* **User Experience:** Ensure form submissions provide clear feedback (though simple redirects will suffice for V1).

### **7\. Deployment**

The application will be deployable on any standard WSGI server (e.g., Gunicorn with Nginx) or platform-as-a-service (PaaS) providers that support Python Flask applications. For local development, flask run will be sufficient.