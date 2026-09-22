# BlueCrest Rotaract Hub PWA

A mobile-first Progressive Web App for managing BlueCrest Rotaract Club members, executives, meetings, attendance, projects, ideas, documents, tasks, finances, presidential plans and handover workflows.

## UI direction
The interface follows the uploaded reference: a clean white campus-management dashboard, left navigation on desktop, compact top bar, card-based statistics, rounded tables, restrained blue branding, and a mobile bottom navigation.

## Included roles
- President
- Vice President
- Secretary
- Project Director
- Treasurer
- Public Image / PRO
- Membership Director
- Sergeant-at-Arms
- Member

## Demo credentials
All demo accounts start with a temporary password and are forced to change it after first login.

| Role | Email | Temporary password |
|---|---|---|
| President | president@bluecrestrotaract.org | BCR-PRES-2026 |
| Vice President | vp@bluecrestrotaract.org | BCR-VP-2026 |
| Secretary | secretary@bluecrestrotaract.org | BCR-SEC-2026 |
| Project Director | projects@bluecrestrotaract.org | BCR-PROJ-2026 |
| Treasurer | treasurer@bluecrestrotaract.org | BCR-TR-2026 |
| Public Image / PRO | pro@bluecrestrotaract.org | BCR-PRO-2026 |
| Membership Director | membership@bluecrestrotaract.org | BCR-MEM-2026 |
| Sergeant-at-Arms | sergeant@bluecrestrotaract.org | BCR-SAA-2026 |
| Member | member@bluecrestrotaract.org | BCR-MEMBER-2026 |

### Password behaviour
1. Each role has a unique temporary password.
2. On first login, the user is forced into the **Set a new password** screen.
3. The new password must be at least 8 characters.
4. The password is stored in this demo's browser localStorage.
5. In production, passwords MUST be handled by Supabase Auth or another secure authentication provider; never store plaintext passwords in a client database.

## Core workflows implemented
- Public member registration → pending queue → Secretary/President/Membership review → member account creation.
- Executive appointment and custom executive positions.
- Role-specific navigation and client-side permission gates.
- Meeting scheduling, meeting start, attendance and minutes workspace.
- Project creation, progress tracking and project proposal workspace entry point.
- Club idea submission, voting and review.
- Treasurer income/expense transaction records and CSV export.
- Presidential Plan of Action progress tracking.
- Club-wide notifications.
- Document centre.
- Task management.
- Presidential handover checklist and handover initiation.
- Audit activity log.

## Run
This is a static PWA and can be opened from a local development server. For service-worker installation, use a local HTTP server such as VS Code Live Server rather than `file://`.

Example:

```bash
python -m http.server 5500
```

Then open `http://localhost:5500` in a browser.

## Production upgrade: Supabase
The current build deliberately uses localStorage so it can run immediately without a backend. Before real club use, migrate to:

- Supabase Auth for email/password and password reset.
- PostgreSQL tables for users, membership applications, roles, meetings, attendance, projects, ideas, documents, tasks, transactions, plans and audit logs.
- Supabase Storage for documents, receipts and project media.
- Row Level Security (RLS) policies for every protected table.
- Server-side validation for role changes and financial approvals.
- Never trust hidden buttons or client-side role checks as security.

Suggested tables:
`profiles`, `membership_applications`, `roles`, `permissions`, `role_permissions`, `executive_positions`, `executive_appointments`, `committees`, `committee_members`, `meetings`, `meeting_attendance`, `meeting_minutes`, `appointments`, `events`, `projects`, `project_ideas`, `project_proposals`, `project_tasks`, `project_members`, `project_reports`, `project_media`, `documents`, `notifications`, `tasks`, `financial_accounts`, `transactions`, `budgets`, `presidential_plans`, `presidential_plan_items`, `handover_records`, `audit_logs`, `club_settings`.

## Important
This is a complete front-end functional PWA build, but authentication and data persistence are intentionally local/demo-only. Do not deploy it for real member or financial data until Supabase Auth, database RLS, secure storage, audit controls and server-side authorization are connected.

use the "logo.png" which is located in icons folder as the icon and "login.png" which is located in Assert folder as the backgroud imageto the left side at the signin page. allow a user to logout