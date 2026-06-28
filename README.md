# Ledger Month — Bill Tracker

A private, on-device tracker for bill due dates and payments. No accounts, no sign-in, no bank passwords. Everything is stored in your own browser, and your data only leaves the device if you choose to export a backup file.

## What it does

- Add bills with an amount, due date, category and optional notes
- Mark bills as one off, weekly, monthly or yearly (the next occurrence is created automatically when you mark a recurring bill paid)
- See a month at a glance: billed, paid, still to pay and overdue
- A month timeline that places each bill on its due day, colour coded by status
- Filter by all, unpaid, overdue or paid, and sort by due date, amount or name
- Mark bills as paid with a payment date and the amount actually paid
- Flag bills that pay automatically (autopay)
- Reconcile against a bank statement CSV that you download yourself (see below)
- Export and import a JSON backup, and switch currency (defaults to OMR)

## A note on connecting to your bank

This app does not connect to any bank, and that is deliberate.

A site published on GitHub Pages is fully public, including its source. The legitimate way apps read bank data is through licensed aggregators such as Plaid or TrueLayer, which require a secret server key and a consent flow that a static page cannot hold safely. Any app that asks for your online banking username and password directly is a genuine security risk and should be avoided.

The safe alternative used here: download a statement as CSV from your banking app, then load it under **Reconcile**. The file is read entirely in your browser, is never uploaded anywhere, and is matched against your unpaid bills by amount so you can confirm which payments actually cleared.

## Deploy on GitHub Pages

1. Create a new repository and upload these files to the root:
   - `index.html`, `manifest.json`, `sw.js`, `icon.svg`
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, pick your branch (usually `main`) and the `/root` folder, then save.
4. Wait a moment, then open the published URL (for example `https://<your-username>.github.io/<repo>/`).
5. On a phone, use **Add to Home Screen** to install it as an app. It works offline after the first load.

## Privacy and backups

Bills live only in this browser via local storage. Clearing site data, using a different browser, or switching device will not carry them across. Export a backup from the **Data** panel regularly, and import it elsewhere to move your data.

## Customising

Everything is in the single `index.html` file: vanilla HTML, CSS and JavaScript, no build step and no external libraries. Edit the seed bills in `seedIfEmpty()`, add currencies in the `CURRENCIES` map, or adjust the colour tokens at the top of the stylesheet.
