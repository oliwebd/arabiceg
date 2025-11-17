---
title: "Settings"
slug: "settings"
icon: "bi-shield-lock"
menu: "main"
weight: 80
author: "OliMiah"
---

{{< rawhtml >}}

<!-- Sync Section -->
<section class="glass-card p-4">
  <h2 class="fw-bold fs-4 mb-3 border-bottom pb-2">
    <i class="bi bi-arrow-repeat me-2 text-success"></i>Sync Phrase Data
  </h2>

  <div class="small text-muted mb-3">
    <p class="fw-bold mb-1">Tap <strong>“Sync Now”</strong> to:</p>
    <ul class="list-group small">
      <li class="list-group-item">📡 Fetch updated phrase data from <code>Online Server</code></li>
      <li class="list-group-item">💾 Save it to your offline device database</li>
      <li class="list-group-item">🕒 Update the sync time shown below</li>
      <li class="list-group-item">✅ Get live success/fail notifications</li>
    </ul>
  </div>

  <div class="d-flex align-items-center gap-3 mb-3">
    <button id="manual-sync-btn" class="btn btn-outline-success btn-sm">
      ⟳ Sync Now
    </button>
    <span class="text-muted small">
      Last sync: <span id="last-sync-time" class="fw-semibold text-alert">Loading...</span>
    </span>
  </div>

  <div id="sync-spinner" class="d-none mb-2">
    <div class="d-flex align-items-center small text-success">
      <div class="spinner-border spinner-border-sm me-2" role="status"></div>
      <span>Syncing in progress...</span>
    </div>
  </div>

  <div class="alert alert-warning small mb-0">
    ⚠️ You don’t need to sync daily. Data auto-refreshes every 24 hours. Only use this if things feel outdated.
  </div>
</section>
<script>
  const langSelect = document.getElementById('languageSelect');
  const syncBtn = document.getElementById('manual-sync-btn');
  const syncSpinner = document.getElementById('sync-spinner');

  // Load saved language on page load
  document.addEventListener('DOMContentLoaded', () => {
    const savedLang = localStorage.getItem('selectedLang');
    if (savedLang) langSelect.value = savedLang;

    // Update last sync time display
    const lastSync = localStorage.getItem('lastSyncTime');
    document.getElementById('last-sync-time').textContent = lastSync ? timeAgo(new Date(lastSync)) : 'Never';
  });

  // Save language on change
  langSelect.addEventListener('change', () => {
    const selectedLang = langSelect.value;
    localStorage.setItem('selectedLang', selectedLang);
    notyfQueue.show('success', `✅ Language preference saved: ${selectedLang.toUpperCase()}`);
  });

  // Handle manual sync button click
  syncBtn.addEventListener('click', async () => {
    if (!db) {
      notyfQueue.show('error', '❌ Local DB not ready.');
      return;
    }

    syncSpinner.classList.remove('d-none');
    try {
      notyfQueue.show('info', '🔁 Manual sync started...');
      await syncPhrasesFromServer(true); // Force sync
      notyfQueue.show('success', '✅ Sync completed successfully!');
    } catch (e) {
      notyfQueue.show('error', '⚠️ Sync failed.');
      console.error('Manual sync error:', e);
    } finally {
      syncSpinner.classList.add('d-none');
      const lastSync = localStorage.getItem('lastSyncTime');
      document.getElementById('last-sync-time').textContent = lastSync ? timeAgo(new Date(lastSync)) : 'Never';
    }
  });
  </script>
{{< /rawhtml >}}