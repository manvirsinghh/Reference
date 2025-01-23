# Jinja template 

Jinja templates in Frappe let you create dynamic content in Markdown (.md) files by mixing static text with variables and logic.
 You can use them to customize web pages, print formats, email templates,and more. 
 They make it easy to display data dynamically, like inserting user
 details or looping through lists, in a clean and flexible way.

**Basic Syntax of Jinja**

Jinja templates allow embedding dynamic content using:

   - Double curly braces ({{ }}) for variables.
   - Curly braces with percent signs ({% %}) for control structures like loops and conditions.
   -  {# #} for comments (even multiline) inside the template.
   -  
**Practical Use Cases in Frappe**

  1)  Email Templates: Use Jinja templates in .md files to create email bodies.
  2)  Print Formats: Render dynamic content for PDF or HTML print formats.
  3)  Web Pages: Use .md files with Jinja to generate web page content dynamically.
