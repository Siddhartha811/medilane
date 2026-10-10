# API (base: /api/v1)

| Method | Route                     | Auth                | Purpose                               |
| ------ | ------------------------- | ------------------- | ------------------------------------- |
| GET    | /health                   | none                | Health check                          |
| POST   | /auth/login               | none                | Doctor/admin login (sets cookies)     |
| POST   | /auth/refresh             | cookie              | Rotate refresh token                  |
| POST   | /auth/logout              | cookie              | Revoke session                        |
| GET    | /auth/me                  | doctor/admin        | Current user                          |
| POST   | /patients                 | none (rate-limited) | Register patient, returns kiosk token |
| POST   | /patients/:id/consent     | kiosk               | Record consent                        |
| POST   | /interviews               | kiosk               | Start interview                       |
| GET    | /interviews/:id/next      | kiosk               | Next question                         |
| POST   | /interviews/:id/answers   | kiosk               | Save answer                           |
| POST   | /interviews/:id/complete  | kiosk               | Finish, trigger summary + red flags   |
| POST   | /documents                | kiosk               | Upload report (image)                 |
| GET    | /visits                   | doctor              | Queue (filters, pagination)           |
| GET    | /visits/:id               | doctor              | Full record                           |
| PATCH  | /visits/:id/status        | doctor              | Update status                         |
| POST   | /visits/:id/prescriptions | doctor              | Create/issue prescription             |
| GET    | /prescriptions/:id/pdf    | signed link         | Download PDF                          |
| GET    | /admin/stats              | admin               | Analytics                             |
| GET    | /admin/audit-logs         | admin               | Audit log viewer                      |
