---
title: ISO-22000
layout: default
---

<h4>Share</h4>

<div class="share-container">
  <!-- Web Share Button -->
  <div id="webShareSection">
    <button id="webShareBtn" class="primary">
      📤 Share
    </button>
    <p id="webShareStatus"></p>
  </div>

  <!-- Fallback: Copy Link Button -->
  <div id="fallbackSection" style="display: none; margin-top: 1rem;">
    <button id="copyLinkBtn" class="secondary">
      📋 Copy Link
    </button>
    <p id="copyStatus"></p>
  </div>
</div>

<script>
  const webShareBtn = document.getElementById('webShareBtn');
  const webShareStatus = document.getElementById('webShareStatus');
  const copyLinkBtn = document.getElementById('copyLinkBtn');
  const copyStatus = document.getElementById('copyStatus');

  const shareData = {
    title: 'ISO-22000 Food Safety Management System',
    text: 'FSMS standard guide.',
    url: "https://realtechsolns.in/fsms"
  };

  // Web Share API (modern browsers)
  if (navigator.share) {
    webShareBtn.addEventListener('click', async () => {
      try {
        await navigator.share(shareData);
        webShareStatus.textContent = '✓ Shared successfully!';
        webShareStatus.style.color = 'green';
      } catch (err) {
        if (err.name !== 'AbortError') {
          webShareStatus.textContent = '✗ Share failed: ' + err.message;
          webShareStatus.style.color = 'red';
        }
      }
    });
  } else {
    // Fallback: Copy to clipboard (always available)
    document.getElementById('webShareSection').style.display = 'none';
    document.getElementById('fallbackSection').style.display = 'block';
    
    copyLinkBtn.addEventListener('click', () => {
      navigator.clipboard.writeText(shareData.url).then(() => {
        copyStatus.textContent = '✓ Link copied!';
        copyStatus.style.color = 'green';
        setTimeout(() => { copyStatus.textContent = ''; }, 3000);
      });
    });
  }
</script>

