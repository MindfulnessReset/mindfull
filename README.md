<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Master the 3-Minute Mental Reset — Free eBook</title>
  <meta name="description" content="The 3-Minute Mental Reset — quick, practical steps to feel calm and focused." />
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <main class="page" role="main">
    <header class="top-headline" role="banner" aria-labelledby="hero-headline">
      <h1 id="hero-headline" class="headline">Master the 3‑Minute Mental Reset</h1>
      <p class="subhead">Instant calm. Clear focus.</p>

      <!-- New CTA directly under the subheadline -->
      <a class="btn header-primary" href="#lead-form">Get Free eBook</a>
    </header>

    <section class="hero" aria-labelledby="hero-headline">
      <div class="center">
        <div class="panel">
          <p class="tiny">Free eBook — quick steps that fit any schedule</p>

          <a class="btn primary-cta" href="#lead-form">Get Free eBook</a>

          <p class="micro">No spam • Unsubscribe anytime</p>
        </div>
      </div>
    </section>

    <section class="lead" id="lead-form" aria-labelledby="lead-heading">
      <div class="lead-inner">
        <h2 id="lead-heading" class="form-title">Get the eBook</h2>

        <!-- Add your endpoint in data-endpoint (Formspree, ConvertKit webhook, Zapier, etc.) -->
        <form id="leadForm" class="lead-form" data-endpoint="">
          <label for="name" class="sr">Name</label>
          <input id="name" name="name" type="text" placeholder="Name" required autocomplete="name" />

          <label for="email" class="sr">Email</label>
          <input id="email" name="email" type="email" placeholder="Email" required autocomplete="email" />

          <button class="btn submit-cta" type="submit">Send Me the Reset</button>

          <p id="formNote" class="form-note" role="status" aria-live="polite"></p>
        </form>
      </div>
    </section>

    <footer class="site-footer" role="contentinfo">
      <div class="footer-inner">
        <small>© 2025 Voice Forward Systems. All rights reserved.</small>
        <nav class="legal" aria-label="Legal">
          <a href="#" onclick="return false">Privacy</a>
          <span aria-hidden="true">•</span>
          <a href="#" onclick="return false">Terms</a>
        </nav>
      </div>
    </footer>
  </main>

  <script>
    (function () {
      const form = document.getElementById('leadForm');
      const note = document.getElementById('formNote');

      form.addEventListener('submit', async function (e) {
        e.preventDefault();
        note.textContent = '';

        const name = form.name.value.trim();
        const email = form.email.value.trim();
        if (!name || !email) { note.textContent = 'Please enter name and email.'; return; }

        const btn = form.querySelector('.submit-cta');
        btn.disabled = true;
        btn.textContent = 'Sending...';

        const endpoint = form.dataset.endpoint && form.dataset.endpoint.trim();
        try {
          if (endpoint) {
            await fetch(endpoint, {
              method: 'POST',
              headers: { 'Content-Type': 'application/json' },
              body: JSON.stringify({ name, email, source: '3-Minute Mental Reset' })
            });
          } else {
            await new Promise(r => setTimeout(r, 600)); // simulate
          }

          btn.textContent = 'Check your inbox';
          note.textContent = 'Thanks — link sent. Check spam if you don’t see it.';
        } catch (err) {
          console.error(err);
          note.textContent = 'Something went wrong. Try again later.';
          btn.disabled = false;
          btn.textContent = 'Send Me the Reset';
        }
      });
    })();
  </script>
</body>
</html># mindfull
