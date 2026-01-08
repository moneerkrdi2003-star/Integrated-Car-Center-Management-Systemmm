# Car Rental Platform 🚗

**A full-stack car rental and sale platform** built with Django (REST API) and React (frontend).

---

## 🚀 Project overview

This project provides backend APIs (Django) and a React frontend (in `frontee`) for users to register, browse cars for rent or sale, request/approve reservations, and manage purchases and rentals.

Main Django apps:
- `accounts` — authentication, registration, profile management
- `cars` — manage cars for sale and for rent
- `reservations` — create and manage reservations

The Django project is in `car_rental/` and the frontend is in `frontee/`.

---

## 🧰 Tech stack

- Python 3.x, Django (REST-style views)
- SQLite (default dev DB at `car_rental/db.sqlite3`)
- React (Create React App) in `frontee/`
- Dependencies are listed in `requierment.txt` (note the filename)

---

## ⚙️ Prerequisites

- Python 3.10+ installed
- Node.js & npm (for the frontend)
- Recommended: create a virtual environment

---

## 🛠️ Backend — Setup (Windows)

1. Create & activate virtualenv:

```powershell
python -m venv venv
venv\Scripts\activate
```

2. Install Python dependencies:

```powershell
pip install -r requierment.txt
```

3. Run migrations and create a superuser:

```powershell
python manage.py migrate
python manage.py createsuperuser
```

4. Start the development server:

```powershell
python manage.py runserver
```

The API will be available at `http://127.0.0.1:8000/` and the Django admin at `http://127.0.0.1:8000/admin/`.

Static media files are served in DEBUG (see `settings.py`), so uploaded car images are available at the configured `MEDIA_URL`.

---

## 🧭 Frontend — Setup

1. Go to the frontend directory:

```bash
cd frontee
```

2. Install dependencies and start dev server:

```bash
npm install
npm start
```

The React app runs by default at `http://localhost:3000/`. Ensure the Django backend is running and CORS is configured (see `frontee/README.md`).

---

## 📡 Key API endpoints

Base API root: `http://localhost:8000/api/`

Accounts (prefix: `api/accounts/`):
- `POST register/` — register a new user
- `POST login/` — obtain session / token (see implementation)
- `POST change-password/`
- `POST logout/`
- `PUT update-profile/`
- `DELETE delete-user/`
- `GET users/` — list users (admin)

Cars (prefix: `api/cars/`):
- `POST sale/add/` — add car for sale
- `PUT sale/update/<car_id>/` — update car for sale
- `DELETE sale/delete/<car_id>/`
- `GET sale/list/` — list cars for sale
- `POST sale/buy/<car_id>/` — buy car
- `POST rent/add/` — add car for rent
- `PUT rent/update/<car_id>/` — update car for rent
- `DELETE rent/delete/<car_id>/`
- `GET rent/list/` — list cars for rent
- `POST rent/car/<car_id>/` — rent a car

Reservations (prefix: `api/reservations/`):
- `POST request/` — request reservation
- `POST approve/<reservation_id>/` — approve
- `POST reject/<reservation_id>/` — reject
- `GET list/` — list all reservations (admin)
- `GET my/` — list my reservations

Example cURL to register:

```bash
curl -X POST http://127.0.0.1:8000/api/accounts/register/ -H "Content-Type: application/json" -d '{"email":"user@example.com","password":"pass123"}'
```

---

## ✅ Running tests

Run Django tests:

```powershell
python manage.py test
```

There are test suites in `accounts`, `cars`, and `reservations`.

---

## 🔧 Development notes

- Database: dev uses SQLite at `car_rental/db.sqlite3`. For production switch to PostgreSQL or another RDBMS.
- If you change CORS or frontend host, update `CORS_ALLOWED_ORIGINS` in `settings.py`.
- Media files: uploaded car images are saved under `media/` (see `settings.MEDIA_ROOT`).
- The `requierment.txt` file name contains a typo; you may rename it to `requirements.txt` for clarity.

---

## 🤝 Contributing

1. Fork the repo and create a branch: `feature/your-feature`
2. Make changes and add tests
3. Open a PR with a clear description

Please follow code style, add tests for new features, and update or add documentation when necessary.

---

## 📄 License

This project is available under the MIT License. Replace with your preferred license if needed.

---

## ✉️ Contact / Authors

- Project created as a Final Project
- For questions, review the `frontee/README.md` or open an issue

---

Thank you for using this project! 💡
