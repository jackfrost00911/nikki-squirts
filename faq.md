---
layout: default
title: FAQ | Nikki Squirtss
permalink: /faq/
---

<div class="faq-container" style="max-width: 800px; margin: 0 auto; padding: 60px 20px;">
  
  <header class="faq-header reveal" style="text-align: center; margin-bottom: 50px;">
    <h1>Common Enquiries</h1>
    <p>Everything you need to know about the bespoke experience I provide. If your question isn't listed, please reach out directly.</p>
  </header>

  <div class="faq-list">
    {% for item in site.data.faq %}
    <div class="faq-item card reveal" style="margin-bottom: 20px; cursor: pointer;">
      <h3 class="faq-question" style="margin: 0; display: flex; justify-content: space-between; align-items: center;">
        <span>{{ item.q }}</span>
        <span class="icon" style="color: var(--gold);">+</span>
      </h3>
      <div class="faq-answer" style="display: none; padding-top: 20px; border-top: 1px solid rgba(255,255,255,0.1); margin-top: 15px;">
        {{ item.a | markdownify }}
      </div>
    </div>
    {% endfor %}
  </div>

  <section class="cta-section reveal" style="background: linear-gradient(135deg, var(--card-bg), #1a1a1a); border: 1px solid var(--gold); padding: 40px; text-align: center; margin-top: 60px; border-radius: 12px;">
    <h2>Ready to begin?</h2>
    <p>Your discretion and satisfaction are my highest priorities.</p>
    <a href="/contact/" class="cta" style="display: inline-block; margin-top: 10px;">Request an Appointment</a>
  </section>
</div>

<script>
  // Simple Accordion Logic
  document.querySelectorAll('.faq-item').forEach(item => {
    item.addEventListener('click', () => {
      const answer = item.querySelector('.faq-answer');
      const icon = item.querySelector('.icon');
      const isOpen = answer.style.display === 'block';
      
      answer.style.display = isOpen ? 'none' : 'block';
      icon.textContent = isOpen ? '+' : '−';
      item.style.borderColor = isOpen ? 'rgba(255,255,255,0.1)' : 'var(--gold)';
    });
  });
</script>
