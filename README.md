# Production Slate & Tracker

A mobile-friendly, single-file web application designed for film and video production. It allows you to import your shot list, track the status of individual shots, and use a fully functional digital clapperboard that automatically updates your data. 

## Features
* **Offline-Ready:** Runs entirely in the browser using local storage. No database required.
* **Smart Importing:** Upload your existing Excel (`.xlsx`) or `.csv` shot lists.
* **Interactive Tracker:** Expandable cards for each shot to update Takes, Status (Pending, Done, Skipped), and Shoot Sequence.
* **Digital Slate:** Swipe-to-navigate clapperboard that syncs with your current shot. Tapping the clapper increments the take, marks the shot as "Done", and auto-assigns the next shooting sequence.
* **Export:** Download the updated `.xlsx` file at the end of the shoot with all your logged takes and statuses.

---

## 📋 Spreadsheet Setup (Crucial)

To ensure the app reads your data correctly, your spreadsheet **must** have the headers in **Row 1**. 

Based on the standard template, here is the exact Column and Row layout you should use:

| Column | Header Name | Description | Required? |
| :--- | :--- | :--- | :--- |
| **A** | `Code` | The unique ID for the shot (e.g., *Lappu - 1 - B*). | **YES** *(App ignores rows if Col A is blank)* |
| **B** | `Scene` | The scene number. | Yes |
| **C** | `Location` | Where the scene takes place. | Optional |
| **D** | `Character` | Who is in the shot. | Yes |
| **E** | `Shot` | The specific shot letter/number. | Yes |
| **F** | `Frame` | Framing (e.g., Wide, Close Up). | Optional |
| **G** | `Camera Angle` | Angle (e.g., High, Eye Level). | Optional |
| **H** | `Shoot Type` | Type of shot (e.g., Action, Dialogue). | Optional |
| **I** | `Description` | What happens in the shot. | Optional |
| **J** | `Notes - Shoot/Edit` | Director or editor notes. | Optional |
| **K** | `Take` | *Auto-updated by the app.* | Leave blank/Optional |
| **L** | `Status` | *Auto-updated by the app.* | Leave blank/Optional |
| **M** | `Shoot Sequence` | *Auto-updated by the app.* | Leave blank/Optional |

> **💡 PRO TIP: Automate Column A (The "Code" Column)**
> Because the app requires Column A to not be blank, you can save time by using an Excel formula to automatically generate your Shot Codes based on your Character, Scene, and Shot columns.
> 
> Simply paste this formula into **Cell A2** and drag it down your sheet:
> ```excel
> =CONCATENATE(D2," - ",B2," - ",E2)
> ```
> *Example Result: If Character is "Lappu", Scene is "1", and Shot is "B", Column A will automatically display `Lappu - 1 - B`.*

**⚠️ Important Rule:** The app uses **Column A** (`Code`) to determine if a row contains actual data. If Column A is completely empty (or its formula results in blank spaces), the app will ignore that entire row. 

---

## 🚀 How to Use

### 1. Import Your Data
1. Open the app in your browser.
2. Tap the **Hamburger Menu** (three lines) in the top right.
3. Select **Import Shots** and choose your `.xlsx` or `.csv` file.
4. Your shots will populate as interactive cards.

### 2. Track Your Shots
* **Expand/Collapse:** Tap any card to view the full description, framing, and notes.
* **Manual Updates:** Use the dropdowns at the bottom of a card to manually set the *Take*, *Status*, or *Sequence*.
* **Filters:** Tap the **Filter icon** in the top navigation to sort shots by Scene, Location, Character, or Status.

### 3. Use the Digital Slate
1. On the tracker view, tap the **Send to Slate** button (the arrow icon) on the shot you are about to film.
2. The app will swipe over to the Clapperboard view, automatically populating the Scene, Take, and Character names.
3. **To Mark a Shot:** Tap the physical clapper graphic at the top of the screen. 
   * It will play a sync beep.
   * It will flash the screen for visual sync.
   * It will automatically mark that shot as **Done** in your tracker and increment the take.

### 4. Export Your Progress
1. Once filming is wrapped for the day, tap the **Hamburger Menu**.
2. Select **Export Data**.
3. The app will download an updated version of your original Excel file (e.g., `Filename_Updated.xlsx`) containing all your new takes, sequence numbers, and completed statuses.

---

## 🛠 Tech Stack
* HTML5 / CSS3 / Vanilla JavaScript
* [SheetJS (xlsx)](https://sheetjs.com/) for reading and writing Excel files.
