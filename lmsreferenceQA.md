# LMS QA

## Prerequisites and Setup

1. **What are the main prerequisites for setting up Frappe Framework?**  
   - Python, MariaDB, Redis, Node.js  
   - Git for version control  
   - Nginx for production  

2. **What is the purpose of the `bench init frappe-bench` command?**  
   It initializes a directory structure for your Frappe app, including folders like `sites`, `apps`, and `logs`. It also sets up the Frappe environment.

3. **What are the key directories created under `frappe-bench`?**  
   - `sites`: Contains site databases and configurations.  
   - `apps`: Holds the source code for your Frappe apps.  
   - `logs`: Stores error and operation logs.  
   - `config`: Contains configuration files.  

---

## DocType Creation and Management

4. **What is a DocType in Frappe?**  
   A DocType is a database model that defines the table structure and behavior within the framework.

5. **Which fields were created for the Article DocType?**  
   - Title (Data)  
   - Content (Text)  
   - Category (Select)  
   - Status (Select)  
   - Publish Date (Date)  

6. **What is the naming convention for Articles?**  
   Articles are named as `Article.#####`, where `#####` is an auto-generated number.

---

## Database and Data Structure

7. **What happens in the database when a new DocType is created?**  
   A corresponding table is created, where each field in the DocType becomes a column.

8. **What are some standard fields in DocTypes?**  
   - `name` (Primary key)  
   - `owner` (Document creator)  
   - `created` and `modified` timestamps  
   - `docstatus` (Document state: draft, submitted, etc.)

9. **What is the purpose of the Link field type?**  
   It establishes a relationship between two DocTypes, functioning like a foreign key.

---

## Permissions and Security

10. **Which roles were created in the Library Management System?**  
    - Librarian  
    - Library Member  

11. **How do permissions differ between Librarians and Library Members?**  
    - Librarians can create, edit, and delete documents.  
    - Library Members can only view their own membership and transaction details.

---

## Controller Methods

12. **What is the purpose of controller methods in DocTypes?**  
    They define business logic at various stages of a document’s lifecycle, such as before saving or submitting.

13. **How was `before_save` used in the Library Member DocType?**  
    It ensured that memberships for the same member do not overlap.

14. **What validations were added in the Library Transaction controller?**  
    - Ensuring articles are available before issuing.  
    - Verifying active memberships for issuing articles.

---

## Types of DocTypes

15. **What is a Submittable DocType?**  
    A DocType that can be finalized (e.g., **Library Membership**).

16. **What is a Single DocType?**  
    A DocType that holds a single record (e.g., **Library Settings**).

---

## Form Scripts and UI

17. **What custom buttons were added to the Library Member form?**  
    Buttons to trigger actions like issuing or returning books.

18. **What is the role of form scripts?**  
    To add dynamic behavior, such as alerts and field validations, to forms.

---

## Portal Pages

19. **How was web view enabled for articles?**  
    By enabling **Has Web View** and **Allow Guest to View** in the DocType settings.

20. **What is the difference between `article.html` and `article_row.html`?**  
    - `article.html`: Full article display.  
    - `article_row.html`: Displays article summaries or lists.

---

## System Integration

21. **How are article status changes tracked?**  
    By updating the **Status** field in the Article DocType.

22. **How is membership validated before issuing articles?**  
    Through the `before_submit` hook, ensuring the membership is active.

---

## Technical Implementation

23. **How are database queries handled in Frappe?**  
    Using Frappe's ORM methods like `frappe.db.get_all()` and `frappe.db.insert()`.

24. **How are validation errors displayed?**  
    Using `frappe.throw()` for custom error messages.

25. **What naming system is used for articles?**  
    Articles are named `Article.#####`, with an auto-generated number.

26. **How is article availability tracked?**  
    Through the **Status** field, which changes depending on whether the article is issued or available.

---

## App Installation and Management

27. **What happens if the `--site` flag is omitted during app installation?**  
    An error occurs because Frappe cannot determine the target site.

28. **What files are updated when an app is installed?**  
    - `site_config.json` for site configuration.  
    - Database tables for the app.

29. **Can an app be installed on multiple sites?**  
    Yes, within the same `frappe-bench`.

30. **What happens if an app installation fails?**  
    Check error logs or use `bench --site <site_name> reinstall`.

31. **What is the role of `hooks.py` during installation?**  
    It defines initialization steps like fixtures and permissions.

32. **How are app dependencies handled?**  
    Through the `requirements.txt` file, specifying packages that must be installed.  

---
