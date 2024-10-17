---
layout: page
title: Calendar Version Generator
---

<button id="generateButton">Generate Calendar Version</button>

<p>Version: <span id="calenderVersionValue"></span></p>

<!-- Include Day.js from a CDN -->
<script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>

<script>
    let now = dayjs();

    let calendarVersion = now.format("YYYYMMDDHHmmssSSS");

    document.getElementById('calenderVersionValue').textContent = calendarVersion;
</script>

---

**cite**: How to include day.js was done via ChatGPT