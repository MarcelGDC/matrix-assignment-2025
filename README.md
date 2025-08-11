# Take-Home Assignment – Laravel + Vue + Tailwind (3–6 hours)

## 🎯 Overview
Your task is to implement a **small, self-contained Laravel module** with:

- API endpoints
- Minimal Vue + Tailwind UI
- Unit & feature tests
- Clean code style and static analysis
- Dockerized environment via Laravel Sail

The domain is a simplified version of a sports betting system (`Event`, `Market`, `Selection`).  
Follow conventions similar to our internal codebase where possible:

- Models under `App\Models\Database`
- Use traits, contracts, and enums if appropriate
- Use factories and seeders
- Maintain a clean, PSR-12 compliant codebase

Timebox: **3–6 hours**. Prioritize clarity, correctness, and maintainability over extra features.

---

## 📦 Requirements

### Domain Entities
**Event** (`App\Models\Database\Event`)
- `id`, `name`, `slug`, `scheduled_at`, `status_id` (enum), `league_id`
- Has many `Market`

**Market** (`App\Models\Database\Market`)
- `id`, `event_id`, `name`
- Has many `Selection`

**Selection** (`App\Models\Database\Selection`)
- `id`, `market_id`, `name`, `odds` (decimal)

> You may define simple enums (e.g., `EventStatusEnum`) and/or traits/contracts if they improve structure.

---

### API Endpoints
**GET `/api/events`**
- Returns paginated events with nested markets and selections
- Supports filters:  
  - `search` (by event name)
  - `status_id`
  - `starts_after` (ISO datetime)

**GET `/api/events/{id}`**
- Returns single event with its markets and selections

**POST `/api/bets`**
- Body:
  ```json
  {
    "selection_ids": [1, 5],
    "stake": 10
  }
