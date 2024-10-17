---
layout: page
title: Calendar Version Generator
---

<button id="generateButton">Generate Calendar Version</button>

<p><b>Version (Format used: YYYY.MM.DD.HHmmssSSS)</b></p>
<p><span id="calenderVersionValue"></span></p>

<!-- Include Day.js from a CDN -->

<script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>

<script>
    function generateCalendarVersion() {
        let now = dayjs();

        let calendarVersion = now.format("YYYY.MM.DD.HHmmssSSS");

        document.getElementById('calenderVersionValue').textContent = calendarVersion;
    }

    document.getElementById('generateButton').addEventListener('click', generateCalendarVersion);

    // Run the function immediately when the page loads

    window.onload = function() {
        generateCalendarVersion();
    };
</script>

---

**cite**: Javascript code to generate was obtained via ChatGPT. I was too lazy to figure it out.