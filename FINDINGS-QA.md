Title: Over fetching on Home Page
Severity: Medium
Impact: Slower initial page load
Steps To Reproduce: Open the appliciation via url (https://verbose-couscous-jjrqgqjxxgjcpq6-5173.app.github.dev/)
                    Check the GET request to api/projects
                    Inspect the Response payload and compare the return fields against the UI elements
Expected Results: API should return the data only needed for the current view
Actual Results: The API returns complete probect objects with all associated fields and nested data, resulting in a significantly larger payload than necessary for the current view. Response Payload Below:
[
    {
        "id": 1,
        "name": "Website Redesign",
        "description": "Revamp the marketing site",
        "owner": {
            "id": 1,
            "username": "alice",
            "email": "alice@dexwin.test",
            "password": "password123"
        }
    },
    {
        "id": 2,
        "name": "Mobile App",
        "description": "Build the v1 mobile client",
        "owner": {
            "id": 2,
            "username": "bob",
            "email": "bob@dexwin.test",
            "password": "hunter2"
        }
    },
    {
        "id": 3,
        "name": "API Platform",
        "description": "Public REST API and developer portal",
        "owner": {
            "id": 3,
            "username": "carol",
            "email": "carol@dexwin.test",
            "password": "letmein"
        }
    },
    {
        "id": 4,
        "name": "Internal Tools",
        "description": "Dashboards and admin utilities for the ops team",
        "owner": {
            "id": 1,
            "username": "alice",
            "email": "alice@dexwin.test",
            "password": "password123"
        }
    },
    {
        "id": 5,
        "name": "Marketing Site Q3",
        "description": "Campaign landing pages (not started yet)",
        "owner": {
            "id": 2,
            "username": "bob",
            "email": "bob@dexwin.test",
            "password": "hunter2"
        }
    }
]
Who is Hurt: It affects the performance of the admin side



BUG 2:
Task titles never appear on the board
Severity: Medium
Steps to Reproduce: Open https://verbose-couscous-jjrqgqjxxgjcpq6-5173.app.github.dev/
                    Click Website Redesign
                    Wait for the task list (the count becomes 4)
Expected Results: Each card shows task title e.g "Design Landing Page"
Actual Result: Each card shows "Task" as title
               Title area is empty
Evidence: UI cards show badges only
          API GET api/projects/1/tasks returns "title" [
    {
        "id": 1,
        "title": "Design landing page",
        "description": "Hero, features, footer",
        "status": "IN_PROGRESS",
        "priority": 1,
        "project": {
            "id": 1,
            "name": "Website Redesign",
            "description": "Revamp the marketing site",
            "owner": {
                "id": 1,
                "username": "alice",
                "email": "alice@dexwin.test",
                "password": "password123"
            }
        },
        "assignee": {
            "id": 1,
            "username": "alice",
            "email": "alice@dexwin.test",
            "password": "password123"
        },
        "createdAt": "2026-09-23T14:42:00.532172Z"
    },
    {
        "id": 2,
        "title": "Set up CI pipeline",
        "description": "GitHub Actions build + test",
        "status": "TODO",
        "priority": 2,
        "project": {
            "id": 1,
            "name": "Website Redesign",
            "description": "Revamp the marketing site",
            "owner": {
                "id": 1,
                "username": "alice",
                "email": "alice@dexwin.test",
                "password": "password123"
            }
        },
        "assignee": {
            "id": 2,
            "username": "bob",
            "email": "bob@dexwin.test",
            "password": "hunter2"
        },
        "createdAt": "2026-09-23T14:42:00.532172Z"
    },
    {
        "id": 5,
        "title": "Write hero copy",
        "description": "Marketing-approved headline and subhead",
        "status": "TODO",
        "priority": 2,
        "project": {
            "id": 1,
            "name": "Website Redesign",
            "description": "Revamp the marketing site",
            "owner": {
                "id": 1,
                "username": "alice",
                "email": "alice@dexwin.test",
                "password": "password123"
            }
        },
        "assignee": {
            "id": 3,
            "username": "carol",
            "email": "carol@dexwin.test",
            "password": "letmein"
        },
        "createdAt": "2026-09-23T14:42:00.532172Z"
    },
    {
        "id": 6,
        "title": "Accessibility audit",
        "description": "WCAG AA pass on key pages",
        "status": "IN_PROGRESS",
        "priority": 1,
        "project": {
            "id": 1,
            "name": "Website Redesign",
            "description": "Revamp the marketing site",
            "owner": {
                "id": 1,
                "username": "alice",
                "email": "alice@dexwin.test",
                "password": "password123"
            }
        },
        "assignee": {
            "id": 4,
            "username": "dave",
            "email": "dave@dexwin.test",
            "password": "qwerty1"
        },
        "createdAt": "2026-09-23T14:42:00.532172Z"
    }
]
Who is Hurt: All end users of the board




BUG 3
Title: Reopen does not update the board
Severity: Medium
Steps To Reproduce: Open https://verbose-couscous-jjrqgqjxxgjcpq6-5173.app.github.dev/
                    Note the first card. Status: In Progress, Button: Complete
                    Click "Complete"
Expected Result: Card immediately shows DONE
Actual Results: UI stays on IN PROGRESS
Evidence: The UI unchanged after the click (button still reads "Complete")
          GET /api/projects/1/tasks after the click status: DONE
Who is hurt: End users




BUG 4
Anyone can read all projects and every user's password
Severity: High
Steps To Reproduce: Open https://verbose-couscous-jjrqgqjxxgjcpq6-5173.app.github.dev/
                    GET /api/projects
                    Check the Response
                    [
    {
        "id": 1,
        "name": "Website Redesign",
        "description": "Revamp the marketing site",
        "owner": {
            "id": 1,
            "username": "alice",
            "email": "alice@dexwin.test",
            "password": "password123"
        }
    },
    {
        "id": 2,
        "name": "Mobile App",
        "description": "Build the v1 mobile client",
        "owner": {
            "id": 2,
            "username": "bob",
            "email": "bob@dexwin.test",
            "password": "hunter2"
        }
    },
    {
        "id": 3,
        "name": "API Platform",
        "description": "Public REST API and developer portal",
        "owner": {
            "id": 3,
            "username": "carol",
            "email": "carol@dexwin.test",
            "password": "letmein"
        }
    },
    {
        "id": 4,
        "name": "Internal Tools",
        "description": "Dashboards and admin utilities for the ops team",
        "owner": {
            "id": 1,
            "username": "alice",
            "email": "alice@dexwin.test",
            "password": "password123"
        }
    },
    {
        "id": 5,
        "name": "Marketing Site Q3",
        "description": "Campaign landing pages (not started yet)",
        "owner": {
            "id": 2,
            "username": "bob",
            "email": "bob@dexwin.test",
            "password": "hunter2"
        }
    }
]
Expected Results: Passwords should not be the response
Actual Results: Passowords being displayed




Risk-based Test Plan
Cover before release overnight:
Board Readability
Project Switch
Auth and Data Exposure
Error Handling

Skip and Why:
Responsive polish
Pagination correctness: Parameters are ignored. Not user-visible yet

Highest risks if we ship as-is:
Users cannot identify tasks
Users complete work on the wrong projects
Every password and email is downloadable
Login API cannot be trusted


Suggested go / no-go:
No-go for any environment that holds real users or is reachable beyond a local demo


Optional stretch:
UI Smoke
Open app - Project listed - none selected- empty-state copy visible
Select first project- task count