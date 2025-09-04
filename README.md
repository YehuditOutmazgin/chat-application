# Chat Application

A lightweight real-time chat application built with **Flask** (Python).  
This app allows user registration, login, room creation, and simple text-based chatting with persistent room logs.  

## Features

- User registration and login (stored in CSV with base64-encoded passwords)
- Multiple chat rooms, created dynamically
- Lobby page listing all available rooms
- Room-based text chat (messages stored in `.txt` files)
- Session management with Flask
- Health endpoint (`/health`) for simple monitoring
- Logout functionality
- Minimal setup and easy to run locally or inside Docker

---

## Project Structure

```

.
├─ chatApp.py          # Main Flask app
├─ requirements.txt    # Python dependencies
├─ templates/          # HTML templates (register, login, lobby, chat)
├─ static/             # CSS, JS, and assets
├─ rooms/              # Chat room logs (\*.txt)
├─ users.csv           # Registered users (username, encoded password)
├─ dockerfile          # Container build file
├─ dockerfiles/        # (Optional) extra docker configs
└─ auto.sh             # Helper script

````

---

## Installation (Local)

### Prerequisites
- Python 3.10+
- pip

### Steps
```bash
# 1. Clone repository
git clone https://github.com/YehuditOutmazgin/chat-application.git
cd chat-application

# 2. Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate   # Linux/macOS
# .\.venv\Scripts\Activate.ps1   # Windows PowerShell

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set environment variables
export ROOM_FILES_PATH="rooms/"
export USERS_PATH="users.csv"

# 5. Run the app
python chatApp.py
````

Now open your browser at:
👉 `http://localhost:5000/`

---

## Running with Docker

```bash
# Build
docker build -t chat-app -f dockerfile .

# Run
docker run --name chat-app --rm -p 5000:5000 \
  -e ROOM_FILES_PATH="/app/rooms/" \
  -e USERS_PATH="/app/users.csv" \
  chat-app
```

---

## Endpoints

* `/register` → Register new user
* `/login` → Login page
* `/logout` → Logout and clear session
* `/lobby` → Lobby and create rooms
* `/chat/<room>` → Join a specific room
* `/api/chat/<room>` → API to fetch/post messages

  * `POST msg=<text>` → add message
  * `POST ?clear=true` → clear messages of current user
* `/health` → Health check (`ok,200`)

---

## Notes

* Messages are stored in plain text files under `rooms/`.
* Users are stored in `users.csv` with base64-encoded passwords (not secure, for demo only).
* For production use, replace password storage with hashing (e.g., bcrypt) and use a proper database.

---

## License

This project is provided **for private use only**.
You may study and use it personally, but redistribution, modification, or commercial use is not permitted without explicit permission.
