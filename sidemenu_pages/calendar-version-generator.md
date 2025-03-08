---
layout: page
title: Calendar Version Generator
category: programming
---

<div style="text-align: center; margin-top: 20px;">
    <button id="generateButton" style="padding: 15px 30px; font-size: 20px; cursor: pointer;">Generate Calendar Version</button>
</div>

<br/>
<br/>
<br/>
<p style="text-align: center;"><b>Version (Format used: YYYY.MM.DD.HHmmssSSS)</b></p>
<p style="text-align: center; font-size: 32px;"><span id="calenderVersionValue"></span></p>

<br/>
<br/>

<p style="text-align: center;"><b>Version (Format used: YYYYMMDDHHmmssSSS)</b></p>
<p style="text-align: center; font-size: 32px;"><span id="calenderVersion1Value"></span></p>

<!-- Include Day.js from a CDN -->

<script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>

<script>
    function generateCalendarVersion() {
        let now = dayjs();

        let calendarVersion = now.format("YYYY.MM.DD.HHmmssSSS");
        document.getElementById('calenderVersionValue').textContent = calendarVersion;

        let calendarVersion1 = now.format("YYYYMMDDHHmmssSSS");
        document.getElementById('calenderVersion1Value').textContent = calendarVersion1;
    }

    document.getElementById('generateButton').addEventListener('click', generateCalendarVersion);

    // Run the function immediately when the page loads

    window.onload = function() {
        generateCalendarVersion();
    };
</script>

---

**cite**: Part of the Javascript code to generate was obtained via ChatGPT. I was too lazy to figure it out.