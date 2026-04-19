# Acentrik Technology Solutions LLC — Website

## Pages
- `index.html` — Home page (hero, services, why us, tech stack, testimonials, FAQ)
- `services.html` — Full services page (all 8 services, IT Consulting, App Modernization, delivery process)
- `about.html` — About page (company story, vision, values, tech expertise, stats)
- `gallery.html` — Portfolio page (6 case studies, case study spotlight)
- `contact.html` — Contact page (form, map, hours, social links)
- `book.html` — Appointment booking (4-step wizard: service → date → time → details)
- `style.css` — Shared stylesheet

---

## Deployment Options

### Option 1: Netlify (Recommended — Free)
1. Go to https://netlify.com and create a free account
2. Drag & drop the entire `acentrik/` folder onto the Netlify dashboard
3. Your site goes live instantly at a `.netlify.app` URL
4. Connect a custom domain (acentriktech.com) in Site Settings → Domain Management

### Option 2: Vercel
1. Go to https://vercel.com, sign up with GitHub
2. Push the folder to a GitHub repo
3. Import the repo in Vercel — it deploys automatically on every push

### Option 3: GitHub Pages (Free)
1. Create a GitHub repo
2. Push all files to the `main` branch
3. Go to Settings → Pages → Source: main branch
4. Live at `yourusername.github.io/reponame`

---

## Contact Form Setup (Formspree)
The contact form currently uses Formspree (free tier: 50 submissions/month).
To activate it:
1. Go to https://formspree.io and sign up
2. Create a new form pointing to `hr@acentriktech.com`
3. Copy your form ID (e.g. `xyyraobk`)
4. In `contact.html`, update the form action:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
5. Done — submissions go directly to hr@acentriktech.com

---

## Appointment Booking — Production Setup
The booking wizard (book.html) is fully functional as a UI demo.
To make it send real emails, add EmailJS:

1. Go to https://emailjs.com and create a free account
2. Create an Email Service linked to hr@acentriktech.com
3. Create an Email Template with variables: `{{service}}`, `{{date}}`, `{{time}}`, `{{name}}`, `{{email}}`, `{{phone}}`, `{{company}}`, `{{notes}}`
4. Add this before `</body>` in `book.html`:
   ```html
   <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
   ```
5. In the `submitBooking()` function, replace the comment with:
   ```javascript
   emailjs.init('YOUR_PUBLIC_KEY');
   emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', {
     service: state.service,
     date: state.date,
     time: state.time,
     name: first + ' ' + document.getElementById('b-last').value,
     email: email,
     phone: document.getElementById('b-phone').value,
     company: document.getElementById('b-company').value,
     notes: document.getElementById('b-notes').value
   });
   ```

---

## Customization Notes
- **Colors**: Edit CSS variables at the top of `style.css` (`:root {}`)
- **Logo**: Replace the `A` in `.logo-icon` with an `<img>` tag once you have a logo file
- **Photos**: All photos are from Unsplash (free to use). To use your own, replace the `url()` values in each page's `<style>` block
- **Address**: 4425 W Airport Fwy, Suite 207, Irving, TX 75062
- **Phone**: +1 (469) 670-4364
- **Email**: hr@acentriktech.com
- **Website**: acentriktech.com
