---
layout: default
title: Request a Reservation | Nikki Squirtss
permalink: /booking/
---

<div class="container" style="max-width: 900px; margin: 0 auto; padding: 60px 20px;">

  <header class="page-header reveal" style="text-align: center; margin-bottom: 60px;">
    <h1 style="font-size: 3.5rem; margin-bottom: 10px;">Request a Reservation</h1>
    <p style="color: var(--gold); letter-spacing: 2px; text-transform: uppercase;">Secure your exclusive time in Reno</p>
  </header>

  <section class="reveal" style="margin-bottom: 60px;">
    <div class="card" style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px;">
      <div class="info-block">
        <h4 style="color: var(--gold);">The Process</h4>
        <p style="font-size: 0.9rem; color: var(--text-muted);">Inquiries are reviewed within 24 hours. For same-day requests, please allow a 2-hour window for a response.</p>
      </div>
      <div class="info-block">
        <h4 style="color: var(--gold);">Discreet Screening</h4>
        <p style="font-size: 0.9rem; color: var(--text-muted);">New clients undergo a verification process. Identity and provider references ensure mutual comfort.</p>
      </div>
      <div class="info-block">
        <h4 style="color: var(--gold);">Confirmation</h4>
        <p style="font-size: 0.9rem; color: var(--text-muted);">A 10% deposit is required to finalize all bookings, fully applied to our time together.</p>
      </div>
      <div class="info-block">
        <h4 style="color: var(--gold);">Cancellation</h4>
        <p style="font-size: 0.9rem; color: var(--text-muted);">Full deposit refund with 48 hours notice. Respect for our schedule is deeply appreciated.</p>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="card" style="background: linear-gradient(145deg, var(--card-bg), #000); padding: 50px;">
      <h2 style="margin-bottom: 30px; text-align: center;">Reservation Details</h2>
      
      <form id="booking-form" action="https://nikki-squirtss-backend.onrender.com/submit-booking" method="POST">
        
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 20px;">
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">First Name *</label>
            <input type="text" name="firstName" required style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
          </div>
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Last Name (Optional)</label>
            <input type="text" name="lastName" style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
          </div>
        </div>

        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 20px;">
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Secure Email *</label>
            <input type="email" name="email" required style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
          </div>
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Phone Number *</label>
            <input type="tel" name="phone" required style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
          </div>
        </div>

        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 20px;">
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Service Type *</label>
            <select name="service" required style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
              <option value="1hour">1 Hour - $320</option>
              <option value="2hour">2 Hours - $620</option>
              <option value="overnight">Overnight Stay</option>
              <option value="couples">Couples Experience</option>
            </select>
          </div>
          <div>
            <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Preferred Date & Time *</label>
            <input type="text" id="date" name="date" required placeholder="Select date..." style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff;">
          </div>
        </div>

        <div style="margin-bottom: 30px;">
          <label style="color: var(--gold); font-size: 0.8rem; text-transform: uppercase;">Specific Requests or Details</label>
          <textarea name="message" style="width: 100%; background: #000; border: 1px solid #333; padding: 12px; color: #fff; height: 100px;"></textarea>
        </div>

        <div style="margin-bottom: 30px; font-size: 0.85rem; color: var(--text-muted);">
          <label><input type="checkbox" required> I agree to the terms of companionship and screening verification.</label>
        </div>

        <button type="submit" class="cta" style="width: 100%; padding: 18px; font-size: 1.1rem; cursor: pointer; border: none;">Submit Invitation</button>
        <p id="booking-status" style="text-align: center; margin-top: 15px; display: none;"></p>
      </form>
    </div>
  </section>
</div>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
<script src="https://cdn.jsdelivr.net/npm/flatpickr"></script>

<script>
  flatpickr("#date", {
    enableTime: true,
    minDate: "today",
    dateFormat: "Y-m-d H:i",
    theme: "dark"
  });

  const form = document.getElementById('booking-form');
  const status = document.getElementById('booking-status');

  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    status.style.display = 'block';
    status.textContent = 'Submitting to Nikki...';
    
    const data = Object.fromEntries(new FormData(form));

    try {
      const response = await fetch(form.action, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data)
      });
      if (response.ok) {
        status.style.color = 'var(--gold)';
        status.textContent = 'Your request has been sent successfully.';
        form.reset();
      } else {
        status.style.color = 'red';
        status.textContent = 'Submission failed. Please try again.';
      }
    } catch (err) {
      status.style.color = 'red';
      status.textContent = 'Error connecting to server.';
    }
  });
</script>
