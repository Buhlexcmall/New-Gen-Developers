# SYSTEM ARCHITECTURE OVERVIEW
## Architecture Style
Layered Architecture
## Alternative Options Considered
- **Monolithic**: Simple to build, one codebase, easy to run, but gets hard to scale features later, and one bug can break everything.
- **Microservices**: Each service scales alone,indipendent deployment, but can be complex for small teams and hard to debug and test.
## Trade-offs
- *Simplicity*: Easy to understand and build for small teams
- *Maintainability*: Clear layers help but the logic can be messy as the project grows
- *Scalability*: all layers scale as one unit
##Potential Architecture Issues
- Single point of failure: A crash in the business logic layer brings the entire application down since all layers are deplyed as one unit
- Tight coupling: If layers bypass each other (e.g. UI querying the database directly), changes in one layer can unexpectedly break another.

  +--------------------------------------------------+
|             STUDENT (Browser / Mobile)           |
+--------------------------------------------------+
                        |
                        v
+--------------------------------------------------+
|              PRESENTATION LAYER                  |
|                                                  |
|  +----------+  +----------+  +---------------+  |
|  | Dashboard|  | Calendar |  |  Assignments  |  |
|  +----------+  +----------+  +---------------+  |
|                                                  |
|  +----------+  +---------------------+           |
|  | Schedule |  |   Notifications     |           |
|  +----------+  +---------------------+           |
|   (React), (HTML & CSS)                          |
+--------------------------------------------------+
                        |
                   HTTP / REST API
                        |
                        v
+--------------------------------------------------+
|             APPLICATION  LAYER                   |
|                                                  |
|  +---------------+  +------------------+         |
|  | Schedule Svc  |  | Assignment Svc   |         |
|  +---------------+  +------------------+         |
|                                                  |
|  +---------------+  +------------------+         |
|  | Notif. Svc    |  | Auth Svc         |         |
|  +---------------+  +------------------+         |
|                                                  |
|  [ Validation | Business Rules | Scheduling ]    |
+--------------------------------------------------+
                        |
                   DB Queries
                        |
                        v
+--------------------------------------------------+
|                  DATA LAYER                      |
|                                                  |
|  +----------------+  +------------------------+  |
|  | Users/Modules  |  | Assignments/Tasks      |  |
|  +----------------+  +------------------------+  |
|                                                  |
|  +----------------+  +------------------------+  |
|  | Schedule/Cal.  |  | Notifications          |  |
|  +----------------+  +------------------------+  |
|                                                  |
|            [ PostgreSQL / MongoDB ]              |
+--------------------------------------------------+


  
  
