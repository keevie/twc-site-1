---
layout: page
title: NYC Local 
permalink: /nyc/
---

# New York City Tech Workers Coalition

We are the New York City local of Tech Workers Coalition. We strive to build worker power and an inclusive & equitable tech industry through rank & file self-organization and education. We discuss and take action on the impacts of technology on workers and communities.

[Subscribe to our calendar!](https://calendar.google.com/calendar?cid=dGVjaHdvcmtlcnNjb2FsaXRpb25ueWNAZ21haWwuY29t){: .calendarlink }

## Upcoming events

<div id='calendar-container'></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.24.0/moment.min.js"></script>
<script>
  const apikey = 'AIzaSyBOuYD41nxrqEFFqrT_M3TgbYVl14BJuc4';
  const calendarUrl = `https://www.googleapis.com/calendar/v3/calendars/techworkerscoalitionnyc@gmail.com/events?key=${apikey}`;

  const calendarContainer = document.getElementById('calendar-container');

  const dateTime2Date = dateString => new Date(new Date(dateString).toDateString());

  const showCalendarEvents = json => {
    const events = json
      .items
      .filter(event => dateTime2Date(event.start.dateTime) > dateTime2Date(Date.now()))
      .sort((a,b) => new Date(a.start.dateTime) - new Date(b.start.dateTime));

    for (const event of events) {
      const eventDiv = document.createElement('div');
      const start = moment(event.start.dateTime).format('LLLL')

      const eventMarkup = `
        <h3>${event.summary}</h3>
        <h3><a href='${event.htmlLink}'>${start}</a></h3>
        <div>${event.location}</div>
      `;

      eventDiv.innerHTML = eventMarkup;
      calendarContainer.appendChild(eventDiv);
    }
  }

  fetch(calendarUrl)
  .then(function(res) {
    return res.json()
  })
  .then(function(res) {
    showCalendarEvents(res);
  });
</script>
