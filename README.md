# Zapier Project

A static patient request form for Prestige Concierge Medicine, built with HTML, CSS, and JavaScript. Request types include prescription refills, appointments, billing, results, referrals, medical records, and general questions.

## Run locally

Open `index.html` in a browser, or serve this folder with Python:

```sh
python -m http.server 8000
```

Then visit `http://localhost:8000`. No build step or package installation is required. Fonts load from Google Fonts.

## Form configuration

Edit the `CONFIG` object near the start of the script in `index.html`:

- `endpoint` is the Webhooks by Zapier Catch Hook URL. Submitting the form sends its fields to Zapier using a form-encoded POST.
- `recipient` is `osaleh28@gmail.com` for every department in this demo.
- Set `endpoint` to an empty string (`""`) to preview submissions locally without sending them.
- `practice` contains the practice name.

Use made-up test information only, as stated on the form. The submission endpoint and any other values in this HTML file are visible to browser visitors.

## Zapier routing

The form includes a routing code in its submission data and email subject. These codes can be used to configure Zapier filters or Paths:

| Code | Request | Department |
| --- | --- | --- |
| RX | Prescription refill | Nurse / Rx line |
| APPT | Appointment | Front desk scheduling |
| BILL | Billing question | Billing office |
| RESULTS | Test results | Clinical team |
| REF | Referral | Referral coordinator |
| RECORDS | Medical records | Medical records |
| GEN | General question | Front desk |

## Finish the Zapier email workflow

1. In the Zap editor, use **Webhooks by Zapier → Catch Hook**. Leave **Pick Off A Child Key** blank. The form already contains the supplied webhook URL.
2. Open `index.html` in a browser, complete the form with made-up information, and submit once.
3. In Zapier's trigger **Test** tab, click **Test trigger** and select that submission.
4. Add **Gmail → Send Email** and connect the Gmail account you want to send from.
5. Set **To** to `osaleh28@gmail.com` (or select the webhook's **Recipient Email** field).
6. Map **Subject** to **Email Subject**, choose a plain text body, and map **Body** to **Email Body**.
7. Test the email action, check the demo inbox, and publish the Zap.

All request types use the same demo inbox, so Paths are optional. The email subject includes `[DEMO]` and the routing code, and the body includes the department and submitted fields. Hidden fields for other request types are excluded.

A successful form submission confirms that the webhook accepted the request. Email delivery still depends on the Gmail action being configured and the Zap being published. In preview mode (`endpoint: ""`), no webhook request or email is sent.

The webhook URL is part of the public client-side source and can be called by visitors. This setup is for the made-up-data demo.

Zapier workflows are configured separately; this repository contains the form only.
