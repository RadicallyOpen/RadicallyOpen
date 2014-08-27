---
permalink: /events/calendar.html
layout: page
html_title: "Radically Open Events Calendar"
title: "Training Events Calendar"
---



<style>
#calendar {
    width: 70%;
    margin: 0 auto;
    margin-left:10%;
}
#calendar h2{
    font-size:14pt;
}
</style>

<script>
$(document).ready(function() {
        $('#calendar').fullCalendar({
            header: {
                left: 'prev,next',
                theme: 'false',
                center: 'title',
                right: 'today'
            },
            {% for event in site.events %}
            {% if forloop.first %}
            defaultDate: "{{event.starts}}",
            {% endif %}
            {% endfor %}
            events: [
                {% for event in site.events %}
                {% for part in event.parts %}
                {
                    title: '{{event.title}} {% if forloop.length > 1 %}(part {{forloop.index}}){% endif %}',
                    start: '{{part.from}}',
                    end: '{{part.to}}',
                    url: '{{event.url}}'
                },
                {% endfor %}
                {% endfor %}
            ]
        });

});



</script>

<div id='calendar'></div>
