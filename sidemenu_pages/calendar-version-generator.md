---
layout: page
title: Calendar Version Generator
---

<button id="generateButton">Generate Calendar Version</button>

<p><b>Version (Format used: YYYYMMDDHHmmssSSS)</b></p>
<p><span id="calenderVersionValue"></span></p>

<!-- Include Day.js from a CDN -->
<script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>

<script>
    function generateCalendarVersion() {
        let now = dayjs();

        let calendarVersion = now.format("YYYYMMDDHHmmssSSS");

        document.getElementById('calenderVersionValue').textContent = calendarVersion;
    }

    document.getElementById('generateVersionBtn').addEventListener('click', generateCalendarVersion);
</script>

---

**cite**: Code to generate was obtained via ChatGPT. I was too lazy to figure it out.