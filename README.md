# Multiplayer Chess

Real-time multiplayer chess in the browser. Players sign up, see who's online, challenge each other with a chosen time control, and play live with server-validated moves, game clocks and in-game chat.

**Live demo:** https://chess-ir64.onrender.com
*(Hosted on Render. The first load can take a few seconds while the server wakes up.)*

## Features

- **Real-time play** over Socket.io, with each game isolated in its own room
- **Server-side move validation** using chess.js, so the server holds the authoritative game state
- **Game clocks** with selectable time controls, plus timeout handling
- **Challenge flow:** live online-player list, send/accept challenges, random color assignment
- **In-game chat** between the two players
- **Auth with email OTP** verification (speakeasy + Nodemailer) and session-based login
- **Match history and player profiles** stored in MongoDB
- **Reconnect handling**, so a dropped player can rejoin an ongoing game

## Tech Stack

| Layer    | Tech |
|----------|------|
| Frontend | React 18, Redux Toolkit, redux-persist, React Router, react-chessboard, Bootstrap |
| Backend  | Node.js, Express, Socket.io, express-session |
| Game logic | chess.js |
| Database | MongoDB (Mongoose) |
| Deploy   | Render |

## Project Structure

```
multiplayer-chess/
├── frontend/          React client
│   └── src/
│       ├── screens/     Home, Play, Game, Login, Register
│       └── components/  Chat, Notifications, OTP, Profile, ...
└── backend/           Express + Socket.io server
    ├── ChessGame.js     game state, move validation, clocks
    ├── routes/          auth (sign-up, sign-in, verify-otp), games, profile
    ├── socket/events/   connect, challenge, accept, join room
    ├── models/          User, Game
    └── database/        queries
```

## Run Locally

**Backend**
```bash
cd backend
npm install
```
Create `backend/.env`:
```
MONGODB_URI=your_mongodb_connection_string
EMAIL_USER=your_gmail_address
EMAIL_PASS=your_gmail_app_password
PORT=3001
```
Then run `node index.js`.

**Frontend**
```bash
cd frontend
npm install
```
Create `frontend/.env`:
```
REACT_APP_API_URL=http://localhost:3001
```
Then run `npm start` and open http://localhost:3000.

## Credits

Co-built with [@Vector73](https://github.com/Vector73).
