---
layout: default
title: Gallery
permalink: /gallery/
---

<h1 style="text-align:center; margin-top:50px;">The Gallery</h1>

<div class="photo-grid reveal">
  <div class="gallery-item">
    <a href="URL_TO_IMAGE" class="glightbox">
      <img src="URL_TO_IMAGE" alt="Nikki" style="width:100%; border-radius:8px;">
    </a>
  </div>
  </div>

<style>
.photo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  padding: 40px 0;
}
.gallery-item img {
  transition: filter 0.3s, transform 0.3s;
  filter: grayscale(20%);
}
.gallery-item img:hover {
  filter: grayscale(0%);
  transform: scale(1.02);
}
</style>
