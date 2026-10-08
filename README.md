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
  Backups/mpn_clinic_data_YYYY-MM-DD.json  ← automatic daily backup
```

## A clinic in five clicks

1. **Virtual Clinic** → **Add patients due by clinic date**.
2. Click **Review** on the first patient. You can paste the FBC from the lab system to fill the results automatically.
3. Choose the dose decision. The regimen and next review date fill in for you.
4. Press **Ctrl+Enter** (Save & complete → next patient). The letter is saved to OneDrive and the next patient opens.
5. When everyone is done, click **Finish clinic**. The secretary pack is saved and the clinic is archived.

## Several people working at once

Saves are merged record by record rather than overwriting the whole file. The app picks up colleagues' changes every 10 seconds. If OneDrive creates a conflict copy (`mpn_clinic_data-PCNAME.json`), the app merges it in and moves it to `Backups/`.

## Troubleshooting

- **The "Connect" button does nothing or reports "not supported".** Use Edge or Chrome. If it still fails, NHS IT policy may block the browser's *File System Access* feature (`FileSystemWriteBlockedForUrls` / `DefaultFileSystemWriteGuardSetting`). Ask IT to allow it for `file://` pages. Until then, the app keeps working in the browser, and you can use **Settings → Export/Import backup** to share data by hand.
- **The data from the previous version is missing.** The app reads the same browser storage as the old version, so your existing data loads automatically. Connect the folder and it is merged into the shared file.

> Information governance: patient data stays on NHS OneDrive and the local PC. Confirm local IG/Caldicott approval before using the app with real patient data.
