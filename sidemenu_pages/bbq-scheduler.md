---
layout: page
title: BBQ Scheduler
---

Enter the time you wish to finish cooking by in the format HH:MM.

<form id="timeForm">
    <label for="completionTime">Completion Time (HH:MM):</label>
    <input type="text" id="completionTime" name="completionTime" placeholder="e.g., 14:30" required>
    <button type="button" onclick="calculateIntervals()">Calculate</button>
</form>

<div id="time-intervals"></div>

<script>
function calculateIntervals() {
    let completionTime = document.getElementById("completionTime").value;;
    
    // Regular expression to validate the time format (HH:MM)
    const timeFormat = /^([01]?[0-9]|2[0-3]):[0-5][0-9]$/;
    
    if (timeFormat.test(completionTime)) {
        displayIntervals(completionTime);
    } else {
        alert("Invalid time format. Please enter a valid time in HH:MM format.");
    }
}

function displayIntervals(endTime) {
    let firstRound = true;

    const intervals = [
        { label: "Prep Meat", minutes: 30 },
        { label: "Clean BBQ", minutes: 30 },
        { label: "Prep Chimney", minutes: 5 },
        { label: "Start Chimney", minutes: 15 },
        { label: "Cook", minutes: 30 },
        { label: "Rest", minutes: 20 },
        { label: "Reheat Fire for Sear", minutes: 20 },
        { label: "Sear", minutes: 20 },
        { label: "Final Rest", minutes: 15 },
        { label: "Finish Cooking", minutes: 0 },
    ];

    let totalMinutes = intervals.reduce((sum, interval) => sum + interval.minutes, 0);
    const endTimeParts = endTime.split(":");
    let endDate = new Date();
    endDate.setHours(parseInt(endTimeParts[0]));
    endDate.setMinutes(parseInt(endTimeParts[1]));

    let htmlContent = `<p>End time: ${endTime}</p><table><tr><th>Description</th><th>Time</th></tr>`;
    
    intervals.forEach(interval => {
        if firstRound {
            firstRound = false;
            continue;
        }
        totalMinutes = totalMinutes - interval.minutes
        let intervalTime = new Date(endDate.getTime() - totalMinutes * 60000);
        let hours = intervalTime.getHours().toString().padStart(2, '0');
        let minutes = intervalTime.getMinutes().toString().padStart(2, '0');
        
        htmlContent += `<tr><td>${interval.label}</td><td>${interval.minutes}</td><td>${hours}:${minutes}</td></tr>`;
    });

    htmlContent += "</table>";
    document.getElementById("time-intervals").innerHTML = htmlContent;
}
</script>
  

<footer style="margin-top: 20px; padding: 10px; background-color: #f0f0f0; text-align: center;">
    <p>**cite**: Javascript code to generate was obtained via ChatGPT. I was too lazy to figure it out.</p>
</footer>