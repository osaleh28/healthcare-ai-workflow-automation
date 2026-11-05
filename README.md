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

- `endpoint` controls where submissions are sent. The current value points to a configured FormSubmit email address. With this value set, submitting the form sends an actual request to that service.
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

Zapier workflows are configured separately; this repository contains the form only.
