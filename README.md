# Archery

An integrated archery app for managing schedules, tracking training and
competition results, accessing lessons, documenting adjustments, and
analyzing progress.

> This project is in its initial setup phase.
> The technology stack and features below describe the planned direction.

## Project Goal

Bring archery schedules, training logs, and competition results together
in one app, helping archers understand their progress over time.

The app aims to connect planning, practice, learning, adjustments, and
analysis so users can review their results and make informed decisions
about their next training session.

## Planned Technology Stack

| Component | Technology / Target | Purpose |
| --- | --- | --- |
| Backend | ASP.NET | APIs, application logic, and data storage and retrieval |
| Frontend | React Native | Mobile screens and user interactions |
| Distribution | Android APK | An installable application for Android devices |

The React Native app will communicate with the ASP.NET backend through
APIs to manage schedules, records, lessons, and other application data.

## Planned Features

| Feature | Goal |
| --- | --- |
| Schedule Management | Organize training sessions, competitions, and other archery activities |
| Record Keeping | Save and review training and competition results |
| Lessons | Provide educational content about archery and training methods |
| Adjustment Tracking | Document archery-related adjustments and changes |
| Performance Analysis | Explore trends, compare results, and identify areas for improvement |

### Schedule Management

- Create and manage training and competition schedules.
- View upcoming activities by date.
- Eventually connect planned activities with completed training records.

### Record Keeping

- Save results from training sessions and competitions.
- Review previous records by date.
- Build a history that helps users reflect on their practice and performance.

### Lessons

- Provide lessons covering archery fundamentals and training methods.
- Help users apply what they learn during practice.
- Define content formats and delivery methods during future design work.

### Adjustment Tracking

- Record and organize archery-related adjustments.
- Preserve a history of changes for reference alongside training results.
- Define the specific adjustment categories and supported workflows
  during future design work.

### Performance Analysis

- Show performance trends using saved training and competition records.
- Support comparisons across different periods.
- Help users identify areas for improvement and plan future training.

## Current Development Status

The repository currently contains an initial Docker-based development
scaffold using React/Vite and Django, adapted from Conchi.

This scaffold precedes the planned transition to React Native and ASP.NET.
The features described above are development goals and are not all
implemented yet.

The setup instructions below apply to the current scaffold.

## Running Locally

Start Docker Desktop, then run the following from the project root:

```sh
cp .env.example .env
docker compose up --build
```

In Windows PowerShell, use `Copy-Item .env.example .env` instead of the first command.

- Frontend: http://localhost:5173
- API health check: http://localhost:5173/api/health/
- Django admin: http://localhost:8000/admin/

Create an administrator account:

```sh
docker compose exec backend python manage.py createsuperuser
```

Stop the services with `docker compose down`.

## Current Scaffold Structure

- `compose.yaml`: Frontend and backend development servers with automatic source change reloading
- `frontend/`: React, Vite, ESLint, and an `/api` backend proxy
- `backend/`: Django, Django REST Framework, CORS, a basic admin interface, and a health check API
- `.env.example`: Example environment variables for the project

Conchi's application code, login functionality, OCR, Firebase and Supabase
connection details, mobile projects, and actual `.env` file were not copied.
The scaffold uses SQLite to start without an external database connection,
with data stored in `backend/db.sqlite3`. The Docker configuration is intended
for local development.

After changing frontend dependencies, refresh the dependency volume with
`docker compose run --rm frontend npm ci`.
