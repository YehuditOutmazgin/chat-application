# Chat Application

A lightweight real-time chat application built with Python and Docker. The project includes HTML/CSS templates for the UI, a Python backend, and containerization assets for easy deployment. The repository structure includes `templates/`, `static/`, `rooms/`, `chatApp.py`, `requirements.txt`, a Dockerfile, and helper scripts. ([GitHub][1])

## Features

* Real-time messaging in browser
* Multiple rooms (see `rooms/`)
* Simple user management (see `users.csv`)
* Containerized with Docker for consistent deploys
* Clear separation of backend (`chatApp.py`) and frontend (`templates/`, `static/`)

## Project Structure

```
.
├─ chatApp.py
├─ requirements.txt
├─ dockerfile
├─ dockerfiles/
├─ auto.sh
├─ users.csv
├─ templates/        # Jinja/HTML views
├─ static/           # CSS/JS/assets
└─ rooms/            # Room definitions / data
```

> Browse the repo to see the latest layout and files. ([GitHub][1])

## Getting Started (Local)

### Prerequisites

* Python 3.10+ and `pip`
* (Optional) Docker 24+ and Docker Compose

### 1) Clone and set up a virtual environment

```bash
git clone https://github.com/YehuditOutmazgin/chat-application.git
cd chat-application

# Create & activate venv (Linux/macOS)
python3 -m venv .venv
source .venv/bin/activate

# On Windows (PowerShell):
# python -m venv .venv
# .\.venv\Scripts\Activate.ps1
```

### 2) Install dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 3) Run the app

```bash
# Common options:
# export FLASK_ENV=development
# export PORT=5000

python chatApp.py
```

Now open `http://localhost:5000/` in your browser (use the port the app prints if different).

## Running with Docker

Build and run the container:

```bash
# Build image using the project's Dockerfile
docker build -t chat-app -f dockerfile .

# Run container (map container port → host port as needed)
docker run --name chat-app --rm -p 5000:5000 chat-app
```

Then visit `http://localhost:5000/`.

> There’s also an `auto.sh` helper script in the repo you can adapt for your workflow. ([GitHub][1])

## Configuration

Environment variables you can use (if applicable in your setup):

* `PORT` – Port for the web server (defaults to 5000 in many Flask apps)
* `FLASK_ENV` – `development` or `production`

> If you add more env vars (e.g., secrets, DB URLs), document them here.

## Data & Users

* `users.csv` can be used to seed or reference users for development/demos.
* `rooms/` can define or persist chat-room info depending on your implementation.

> Adjust these files/formats as your app evolves.

## Development Tips

* Keep UI assets in `static/` and views in `templates/`.
* Add unit tests and a `Makefile`/`Justfile` if you plan to extend the project.
* Consider adding linting/formatting (e.g., `ruff`, `black`) to streamline contributions.

## Roadmap

* Authentication hardening
* Message persistence (DB)
* Typing indicators / presence
* CI workflow (GitHub Actions) and container publishing

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you’d like to change. Make sure to update tests and documentation as needed.

## License

Add a license file (e.g., MIT) if you intend for others to use or modify the project.

## Acknowledgments

* Python & Flask ecosystem
* Docker community

---

[1]: https://github.com/YehuditOutmazgin/chat-application "GitHub - YehuditOutmazgin/chat-application: A project in git and docker"
