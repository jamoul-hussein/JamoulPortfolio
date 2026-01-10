# JamoulPortfolio
My personal portfolio (Vue 3 + Vite + Tailwind).

## Run locally

```bash
npm install
npm run dev
```

## Contact form email (EmailJS)
This project sends contact emails via **EmailJS** (no custom backend required).

1. Create an account and set up a **Service** + **Email Template** in EmailJS.
2. Create a `.env` file in the project root with:

```bash
VITE_EMAILJS_SERVICE_ID=your_service_id
VITE_EMAILJS_TEMPLATE_ID=your_template_id
VITE_EMAILJS_PUBLIC_KEY=your_public_key
```

3. In your EmailJS template, add these variables (or rename to match your template):
- `from_name`
- `reply_to`
- `message`
