# 47 Costing, Invoice & Quotation App

A static GitHub Pages-ready app for FORM47, NEXUS47 and HAVEN47.

## Main features

- 3D-print costing by material price, part weight, print time and raw/hand-painted finish
- Machine, electricity, labour, failure allowance, packaging and target-margin settings
- Recommended selling price
- Multi-item invoices and quotations
- Manual unit-price entry for new items
- Manual price editing for items already added to an invoice/quotation
- FORM47 / NEXUS47 / HAVEN47 category selection with matching logo
- Printable A4 invoice and quotation
- Quotation bank details and automatic 50% advance amount
- Client email templates that include the client name and order item names
- Send invoice/quotation emails from one of these accounts:
  - 4orm.4orty.7even@gmail.com
  - nexus.4orty.7even@gmail.com
  - haven.4orty.7even@gmail.com
- Invoice/quotation PDF attachment generated automatically when sending via Gmail

## Run / deploy

Upload `index.html` and the `assets` folder together to your GitHub Pages repository. The normal calculator, invoice and quotation features work as a static site.

## One-time Gmail sending setup

Google does not allow a public web page to send from a Gmail account using only an email address/password. This app therefore uses Google's official OAuth flow and the Gmail API. Do not put your Gmail password or App Password into the app.

1. Open Google Cloud Console and create/select a project.
2. Enable **Gmail API** for the project.
3. Configure the Google OAuth consent screen / Google Auth Platform.
4. If the app is in Testing mode, add these Gmail accounts as test users:
   - 4orm.4orty.7even@gmail.com
   - nexus.4orty.7even@gmail.com
   - haven.4orty.7even@gmail.com
5. Create an **OAuth 2.0 Client ID** with application type **Web application**.
6. Add your GitHub Pages origin as an **Authorized JavaScript origin**, for example:
   `https://YOUR-GITHUB-USERNAME.github.io`
7. Copy the Client ID ending in `.apps.googleusercontent.com`.
8. Paste it into the **Google OAuth Client ID** field in either the Invoice or Quotation email section. The app saves the Client ID in that browser and mirrors it to both sections.
9. Press **Send email + invoice PDF** or **Send email + quotation PDF**. Google will ask you to choose/authorize the selected sender account.

The app requests only the Gmail `gmail.send` scope. Access tokens are kept only in memory for the current page session and are not saved to localStorage.

## Email workflow

For an invoice, the generated message tells the client the order is ready, addresses them by name, lists the invoice item name(s), and attaches the invoice PDF.

For a quotation, the generated message lists the quoted item(s), quotation total and 50% advance required to start the print process, and attaches the quotation PDF.

Use **Regenerate message** after changing client/order details if you want the default template rebuilt. The subject and message can also be edited manually before sending.

## Data

Costing settings, document details, item lists, bank details and the OAuth Client ID are stored in browser localStorage. Gmail access tokens are not stored.
