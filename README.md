# The Shrinking Contract · ELA #2

Classroom bargaining game for Strategy, Unit 2. A Firm and its Supplier split a contract surplus of $5,000 that shrinks by 10% every time a proposal is rejected, over at most nine rounds (an odd number, so the Firm, which proposes first, also makes the last proposal). Rounds, surplus, shrink and the number of teams can be changed on the setup screen.

The same page runs in two ways:

- **Live**: each team uses one phone or laptop. Needs a free Firebase Realtime Database (setup below).
- **This laptop only**: teams write on paper slips and you type each decision. No internet needed. This works even if you open `index.html` straight from your Mac.

Files:

| File | What it is |
|---|---|
| `index.html` | The app: instructor console, team screens, results, theory |
| `config.js` | Your database address (one line to fill in) |
| `firebase-rules.json` | Access rules to paste into Firebase |

## One-time setup (about 10 minutes)

### 1. The database (Firebase, free)

1. Go to <https://console.firebase.google.com> and sign in with any Google account.
2. Create a project, for example `ela2-bargaining`. Google Analytics is not needed: switch it off.
3. In the left menu open **Realtime Database** (under *Build*, or *Databases & Storage* in newer menus) and click **Create Database**. Location: **Belgium (europe-west1)**. Security rules: **Start in locked mode**. Click **Enable**.
4. Open the **Rules** tab, replace everything with the contents of `firebase-rules.json`, and click **Publish**.
5. Open the **Data** tab and copy the address shown at the top. It looks like `https://ela2-bargaining-default-rtdb.europe-west1.firebasedatabase.app`.

The free Spark plan is enough and asks for no card.

### 2. The page (GitHub Pages)

1. On GitHub: **New repository**, name `ela2`, **Public**, **Create repository**.
2. Click **uploading an existing file**, drag in the four files of this folder, and click **Commit changes**.
3. Open `config.js` in the repository, click the pencil icon, paste the database address between the quotes, and click **Commit changes**.
4. **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch **main**, folder **/(root)**, and **Save**. After a minute or two the page is live at `https://efatas.github.io/ela2/`.

### 3. Five-minute check

1. On your laptop open `https://<your-github-user>.github.io/ela2/#console`, choose **Live**, click **Test the connection**, then **Create session**.
2. On your phone, scan the QR code and pick Team 1. In a second browser window (or a colleague's phone) open the same link and pick Team 2.
3. Click **Start Game 1**. Propose from Team 1, reject from Team 2, then accept Team 2's counter-proposal. Look at **Results** and **Data**.
4. Click **Setup** and discard the test session. The class gets a fresh one.

## In class

1. Open `…/ela2/#console` on the laptop connected to the projector and create a **Live** session. The **Join** tab shows a QR code and a short code.
2. Each team chooses one device, scans the code and picks its team number. The Join tab shows who is connected.
3. Project **Rules**, then the **Board**, and click **Start Game 1**. Amounts stay hidden on the board until a game ends; **Show amounts** reveals them.
4. When Game 1 ends, **Start Game 2** swaps roles and gives every team a new partner.
5. **Results** and **Theory** are for the debrief. **Data** copies every proposal as CSV.

If a team's device fails, use **Release device** on the Join tab (another phone can then take over) or **Type for a team** on the Board. **Undo last change** reverses a mistaken entry. If the Wi-Fi fails altogether, go to **Setup**, create a session in **This laptop only** mode, and use the paper slips.

## Notes

- The free plan allows 100 simultaneous connections. One device per team needs six, so do not ask every student to open the link.
- Each session is stored under `ela2/<session code>` in your database. You can delete old sessions from the Firebase **Data** tab at any time.
- Teams appear only by team name; no student names are needed.
- The game logic, the live connection and the results were tested against a local stand-in for Firebase that follows its REST and streaming protocol. The five-minute check above is the first run against your own database.
