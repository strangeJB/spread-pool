# spread-pool

A single-file web app for tracking a 64-team NCAA spread pool bracket. Open `spread-pool-bracket.html` in any browser — no server, no install, no dependencies.

---

## How the Pool Works

Each of the 64 teams is assigned to an owner before the tournament. The spread-pool twist changes who advances:

- **If the favorite wins and covers the spread** → the favorite's owner advances, riding the winning team.
- **If the underdog loses but beats the spread (or wins outright)** → the underdog's owner advances, now riding the winning team going forward.
- **All ties go to the underdog.**

Owners follow their spread-winner through each round, potentially switching teams as upsets happen. Spreads lock once a game starts.

---

## Participants

**Main Bracket (32 players, 64 teams):**
Abi, Alan, Amy, Ashley, Becca, Betsy, Boris, Brian P, Brian T, Callie, Caroline, Cassie, David, Eric, Ethan, Henry, Jake, Jon, Jonathon, Josh, Julie, Kelsey, Lori, Mike F, Mike H, Morgan, Nick, Rachel, Ron, Steph, Tim, Troy

**Loser's Bracket (16 players, 16 teams — Sweet 16 onward):**
Abi, Amy/Jon, Becca, Boris, Callie, Cassie, David/Caroline, Eric, Jake, Lori/Henry, Morgan, Nick, Rachel, Steph, Tim, Troy

---

## Features

### Main Bracket
- All four regions (East, South, West, Midwest) plus Final Four and Championship
- Live scores auto-refresh every 15 seconds during active games, every 3 minutes otherwise
- Spread-pool ownership tracked through every round — owner names update as teams advance
- Covered highlight: when an underdog covers, the advancing team name turns orange
- **Hide/Show Early Rounds** floating button (bottom-right) collapses First and Second Round columns to focus on the Sweet 16+
- On mobile portrait, hiding early rounds switches to a narrow two-column layout that fits the screen without horizontal scrolling

### Loser's Bracket
- Separate bracket starting at the Sweet 16 with a parallel set of 16 owners
- Accessible via the hamburger menu (☰)
- Same spread-pool logic, same live score updates

### Players View
- Card grid showing every owner's current teams, status, and which round they're in
- Color-coded: green = alive/won, yellow = upcoming, red = eliminated
- Click any team row to jump directly to that game in the bracket

### Search
- Search by owner name or team name
- Results show clickable game cards that scroll and highlight the target game
- Works in both Main and Loser's bracket views
- Auto-expands hidden early rounds when navigating to a First or Second Round game

---

## Live Data

Scores are fetched from the ESPN public API via several CORS proxies tried in sequence. The bracket always renders from hardcoded known results first, then layers live data on top — so it's never blank even if the API is unavailable.

**Best served over HTTP** (e.g. `node serve.js` then open `http://localhost:8080`) rather than opened directly as a `file://` URL, which blocks cross-origin requests in Chrome.

---

## Tournament Dates

| Round | Dates |
|---|---|
| First Round | Mar 19–20 |
| Second Round | Mar 21–22 |
| Sweet 16 | Mar 26–27 |
| Elite 8 | Mar 28–29 |
| Final Four | Apr 4 |
| Championship | Apr 6 |
