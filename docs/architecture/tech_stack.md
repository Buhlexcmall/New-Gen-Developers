# Technology Stack — SmartStudy

## Stack Summary

| Layer | Technology | Version |
|-------|-----------|---------|
| Frontend | React.js | 18.x |
| Backend | Python / Django REST Framework | Python 3.11, Django 4.x |
| Database | PostgreSQL | 15.x |
| Hosting (Staging) | Railway / Render | Cloud PaaS |
| Hosting (Production) | AWS EC2 + AWS RDS | Cloud IaaS |
| Version Control | GitHub | — |
| Design / Prototyping | Figma | — |
| API Testing | Postman | — |

---

## Justification

### Frontend: React.js
React.js was chosen because it uses a component-based architecture, which means UI elements like the assignment list, schedule calendar, and dashboard can each be built as reusable, independent components. React's virtual DOM ensures fast re-rendering when data changes (e.g. when a student updates an assignment status). It has a large community, extensive documentation, and is widely used in industry, giving team members transferable skills.

### Backend: Python / Django REST Framework
Django was selected for its "batteries included" philosophy — it provides built-in tools for user authentication, database migrations, admin panel, and API routing. The Django REST Framework (DRF) extension makes it straightforward to build the JSON API that the React frontend will consume. Python is already familiar to most Computer Science students, reducing the learning curve. Django's ORM simplifies database interaction without writing raw SQL.

### Database: PostgreSQL
PostgreSQL is a powerful, open-source relational database that handles structured academic data (students, assignments, schedules) reliably. It supports complex queries, indexing (important for sorting assignments by due date), and enforces data integrity through foreign key relationships. It integrates seamlessly with Django through its ORM.

### Hosting: Railway/Render (Staging) and AWS (Production)
Railway and Render offer free-tier cloud hosting that is ideal for testing and demonstrating the app during development. For a production environment, AWS EC2 (application server) and AWS RDS (managed PostgreSQL database) provide the scalability, reliability, and uptime guarantees needed for a real deployment. This mirrors the industry-standard pattern shown in the deployment diagram.

### Version Control: GitHub
GitHub provides source control, collaboration features (pull requests, code reviews), issue tracking, and the GitHub Projects board used for Agile task management throughout the project.

### Design / Prototyping: Figma
Figma is an industry-standard UI/UX design tool that allows the team to collaboratively design and share wireframes and prototypes before any code is written. It is browser-based and free for student teams.

### API Testing: Postman
Postman allows the backend team to test API endpoints independently of the frontend during development, speeding up debugging and ensuring all endpoints behave correctly before integration.

---

## Technology Stack Diagram

```
+-------------------+        +----------------------+       +------------------+
|   React.js        |  HTTP  |  Django REST API      | SQL   |  PostgreSQL DB   |
|   (Frontend)      | <----> |  (Backend / Python)   | <---> |  (Data Layer)    |
|   Vercel / CDN    |        |  AWS EC2              |       |  AWS RDS         |
+-------------------+        +----------------------+       +------------------+
```

> A digital version of the full deployment diagram is available in docs/architecture/diagrams/
