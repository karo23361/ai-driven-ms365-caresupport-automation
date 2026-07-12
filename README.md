# AI-Driven-MS365-CareSupport-Automation


I’ve built a small support automation system using Microsoft 365 tools.
The idea is to connect SharePoint, Power Automate, Power Apps and a <b> Copilot Studio Agent </b> to handle support cases in a simple way.

<h1> Copilot Studio - Workflow </h1>
<img width="2065" height="614" alt="image" src="https://github.com/user-attachments/assets/c545e504-ae91-460d-afef-e3a7414a6eef" />


<h2>1. Trigger: New Email in Shared Mailbox</h2>
<p>
The workflow starts automatically when a new email arrives in the shared mailbox 
<strong>care@company.com</strong>.
</p>

<h2>2. AI Agent Classification</h2>
<p>
The workflow sends the email details (subject, body, sender, received time) to the AI Agent.
The agent analyzes the message and returns:
</p>
<ul>
  <li>Category</li>
  <li>Subcategory</li>
  <li>SLA_BreachRisk</li>
  <li>Title</li>
  <li>Tags</li>
  <li>Priority</li>
</ul>

<h2>3. Conditional Logic (IF / ELSE)</h2>
<p>The workflow checks the AI‑generated value <strong>SLA_BreachRisk</strong>.</p>

<h3>IF SLA_BreachRisk = 1 (High Risk)</h3>
<ul>
  <li>Create a case item in the SharePoint list</li>
  <li>Send a notification email to 1st line support (from shared mailbox; in a real project this would use a proper contact table)</li>
</ul>

<h3>ELSE (Standard Case)</h3>
<ul>
  <li>Create a case item in the SharePoint list</li>
  <li>No notification is sent</li>
</ul>

<h2>4. Create SharePoint Case Item</h2>
<p>
Both branches create a SharePoint list item containing the AI‑generated metadata and email details.
</p>

<h1>Agent Configuration</h1>
<p>
The agent was prepared as a simple read‑only support assistant: it was given access to the SharePoint ticket database and instructed to only interpret and explain ticket fields without modifying anything. It was connected to the workflow through basic input variables (email data) and output variables (classification results).
</p>


<img width="1159" height="864" alt="image" src="https://github.com/user-attachments/assets/c47f2da3-3b0d-4a25-97d4-e1d60cbbefb7" />

<h1> Canvas App - Power Apps </h1>
<p> 
The really simple draft app was prepared to present usage of generated data in tool by care support. Of course we can go further with more complex logics / automations (automatic notification on status change and reminders). 
</p>

<h2>Page - Case List </h2>

<img width="1294" height="732" alt="image" src="https://github.com/user-attachments/assets/75c20050-9001-40dc-9088-dea12918e1f6" />

<h2>Page - Form </h2>

<img width="1324" height="722" alt="image" src="https://github.com/user-attachments/assets/86ab8df3-86b1-4525-88c7-f3210b86f357" />

