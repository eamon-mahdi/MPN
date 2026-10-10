# MPN Virtual Clinic

A single-file app (`MPN_Virtual_Clinic.html`) for running the hydroxycarbamide MPN virtual clinic. It keeps all its data in a shared **OneDrive / Teams folder**, so it needs no server, install or admin rights.

## One-time setup (service lead)

1. Create a folder in a OneDrive or Teams/SharePoint library that the whole team can access, e.g. `MPN Clinic`.
2. Put `MPN_Virtual_Clinic.html` in that folder.
3. Make sure each team member has the folder **synced to their PC**:
   - For OneDrive, it shows up in File Explorer automatically.
   - For Teams/SharePoint, click **Sync** or **Add shortcut to My files**.

## Each person, first time (about 1 minute)

1. In File Explorer, open the synced `MPN Clinic` folder and open `MPN_Virtual_Clinic.html` in **Microsoft Edge** (right-click → Open with → Edge).
   - Don't open it from the OneDrive website, because scripts won't run there.
2. Click **Connect OneDrive folder**, choose the `MPN Clinic` folder, and click **Edit files / Allow**.
3. Go to **Settings & Sync** and enter your name. This becomes your default reviewer signature.

After that, every time you open the app you only need to click **Reconnect** once. Edge requires this click for security.

## What ends up in the folder

```
MPN Clinic/
  MPN_Virtual_Clinic.html
  mpn_clinic_data.json                  ← the shared database (saved automatically)
  Letters/2026-10-15/
      Smith_John_A123456.doc             ← each letter, written when you save the visit
      _ALL_LETTERS_2026-10-15.doc        ← all letters in one file for printing
      _CLINIC_SUMMARY_2026-10-15.doc     ← summary for the secretary
      _PRESCRIPTIONS_2026-10-15.doc      ← every prescription needed from that clinic
  Backups/mpn_clinic_data_YYYY-MM-DD.json  ← automatic daily backup
```

## Running a clinic (clinics are on Thursdays)

1. **Virtual Clinic** → **Add due patients**. To add anyone else, click **＋ Add**, then:
   - search for the patient and press Enter, or
   - click **New patient** to create someone not yet in the database (it adds them to the clinic straight away), or
   - paste a list of hospital numbers.
2. **🧪 Paste bloods for the whole clinic**: paste the lab report or export once, check the matched results, then click **Apply**. Each patient's results fill in automatically when you open them.
3. Open each patient and click a decision.
   - **Increase/Reduce** opens the **dose builder**. Click a daily dose, alternate-day doses, or a dose for each day of the week, and add any instructions. It writes the wording for the letter and the prescription.
   - When you save, the new dose replaces the current regimen in the patient's record.
4. Tick **Prescription written now** if you have the pad. If not, leave it unticked and it goes on the **Prescriptions** list.
5. Press **Ctrl+Enter** to complete and move to the next patient. The letter is saved to OneDrive.
6. When everyone is done, a green banner appears. Click **Finish & archive** to save the secretary pack and start next Thursday's clinic.

Later, open **Prescriptions** to see every prescription still to write, across all clinics. You can tick them off one by one or mark a whole clinic as written, and you can print the list or save it as a Word file.

## Saving

Everything saves automatically within about 2 seconds, including half-finished reviews, which are kept as drafts and restored when you reopen the patient. **💾 Save all** saves immediately. The top bar shows when the last save happened.

Anyone with **edit** access to the shared OneDrive folder can save. People with view-only access will see a message that their changes couldn't be saved.

## Appearance

Use the switch in the top bar to choose **Light**, **Dark** or **Black** (pure black). The choice is remembered on each computer.

## Training

Fictional demo patients are under **Patients → 🧪 Training / demo data** (at the bottom of the page). Remove them before real clinics.

## Several people working at once

Saves are merged record by record rather than overwriting the whole file. The app picks up colleagues' changes every 10 seconds. If OneDrive creates a conflict copy (`mpn_clinic_data-PCNAME.json`), the app merges it in and moves it to `Backups/`.

## Troubleshooting

- **Edge says “can't open this folder because it contains system files”.** You picked a folder the browser protects: Desktop, Documents, Downloads, your user folder or the top level of OneDrive. Choose a folder *inside* one of those instead. In the picker, go into OneDrive (or Desktop), click **New folder**, name it `MPN Clinic`, open it and click **Select folder**. Keep `MPN_Virtual_Clinic.html` in that same folder.
- **The "Connect" button does nothing or reports "not supported".** Use Edge or Chrome. If it still fails, NHS IT policy may block the browser's *File System Access* feature (`FileSystemWriteBlockedForUrls` / `DefaultFileSystemWriteGuardSetting`). Ask IT to allow it for `file://` pages. Until then, the app keeps working in the browser, and you can use **Settings → Export/Import backup** to share data by hand.
- **The data from the previous version is missing.** The app reads the same browser storage as the old version, so your existing data loads automatically. Connect the folder and it is merged into the shared file.

> Information governance: patient data stays on NHS OneDrive and the local PC. Confirm local IG/Caldicott approval before using the app with real patient data.
