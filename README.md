# Who Killed Mr. X? · Math 3 Escape Room

An online escape room for Ms Badmus's Math 3 classes (Units 1–4 recall).
Teams join on one Chromebook, open four locked doors (Unit 1, 2, 3, 4) by answering
questions, rule out rooms, weapons and suspects, and make an accusation to escape.
The teacher dashboard shows every team live.

* **Students:** `index.html` (the link you give them)
* **Teacher:** `dashboard.html` (same link with `/dashboard.html` on the end)

---

## Set-up (about 10 minutes, once)

### Step 1 · Make the Google Sheet that stores the progress

Use **badmuslyn@gmail.com** (your school account blocks this kind of thing).

1. Go to **sheets.new** and name the sheet `Mr X Escape Room`.
2. Click **Extensions → Apps Script**.
3. Delete what is in the editor. Open the file `apps-script/Code.gs` from this folder, copy all of it, and paste it in.
4. On line 8, change `'2103'` to a PIN of your own if you want (you type it on the dashboard). Click **Save**.
5. Click **Deploy → New deployment**. Click the gear next to "Select type" and choose **Web app**.
   * Description: `Mr X`
   * Execute as: **Me**
   * Who has access: **Anyone**
6. Click **Deploy**, then **Authorize access**. Choose your Gmail account. Google warns that the app isn't verified (it's yours, so that's expected): click **Advanced → Go to Mr X Escape Room (unsafe) → Allow**.
7. Copy the **Web app URL** (it ends in `/exec`).
8. Check it works: paste that URL into a new tab. You should see `"Who Killed Mr. X? is connected."`

### Step 2 · Put the link into the game

Open `js/config.js` and paste the URL between the quotes:

```js
API_URL: "https://script.google.com/macros/s/XXXXXXXX/exec",
```

Save the file.

### Step 3 · Put it on GitHub

1. On github.com click **New repository**. Name it `mr-x`, set it to **Public**, and click **Create repository**.
2. Click **uploading an existing file** and drag in **everything inside this folder** (index.html, dashboard.html, README.md and the css, js, fonts, img, vendor and apps-script folders). Click **Commit changes**.
3. Go to **Settings → Pages**. Under "Branch" choose **main** and **/ (root)**, then **Save**.
4. After a minute the page shows your link, for example `badmuslyn.github.io/mr-x`.

* Student link: `badmuslyn.github.io/mr-x`
* Your dashboard: `badmuslyn.github.io/mr-x/dashboard.html`

**Test it on a student Chromebook before Friday** (school filters sometimes block new sites).

---

## Running it in class

1. Open the dashboard, type a **game code** for the class (for example `B2` for Block 2) and your PIN.
2. Write the student link and the game code on the board (no QR code needed).
3. Teams of 3 or 4 join on **one Chromebook** with a team name and every detective's name. They can read the case and the suspects while they wait.
4. Click **Start the clock**. Every team's game opens at the same moment.
5. Watch the dashboard: doors opened, questions solved, wrong answers, hints, time, and **"Stuck on Q…"** for questions with 2 or more wrong answers. A team with no signal for over a minute turns pink.
6. Click **Projector view** for the big leaderboard. The first team to escape is shown with the prize: **+5 extra credit points on the Unit 4 Quiz grade**.
7. For the next block, use a new game code (for example `B4`). To wipe a game, open **••• → Clear this game**.

**Try the demo:** on the dashboard's first screen, click **Try the demo**, then **Start the clock**. It runs made-up teams so you can see how it works.

## The rules built in

* Every answer is a whole number from 1 to 26 and becomes a letter (A = 1 … Z = 26). The letters spell the code for the door.
* Door 1 (Unit 1) → BY THE BOOKS → the room · Door 2 (Unit 2) → IN HIS CUP → the weapon ·
  Door 3 (Unit 3) → IN GLASSES → two suspects left · Door 4 (Unit 4) → HAD A KITE → the killer.
* Answer: **Carlos (dressed as Benjamin Franklin), in the Library, with the Poisoned Sweet Tea.**
* A hint shows the first step and adds 1 minute. Two wrong answers on one question lock it for 30 seconds.
* A wrong choice after a code adds 1 minute; a wrong accusation adds 2 minutes.
* Change any of these numbers in `js/config.js`.
* If a Chromebook is refreshed or closed, the team carries on where it stopped (progress is saved on the device).
* If the internet drops, the game keeps working; the dashboard catches up when it comes back.

## If something isn't working

* **Dashboard says it can't reach the Google Sheet:** check the link in `js/config.js` ends in `/exec`, and that the deployment is shared with **Anyone**.
* **You changed Code.gs:** click **Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy**, or the old code keeps running.
* **Team names and progress** are also in the Google Sheet (tab `Teams`) if you want a record.
