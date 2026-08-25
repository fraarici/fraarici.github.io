---  
layout: page  
title: events
permalink: /events/  
description: here you can find a list of upcoming and past events.
nav: true  
nav_order: 6  
---  
  
{% assign future_conferences = site.events | where_exp: "item", "item.date >= site.time" | sort: 'date' %}  
{% assign past_conferences = site.events | where_exp: "item", "item.date < site.time" | sort: 'date' | reverse %}  

### Upcoming Conferences and Workshops

  {% if future_conferences.size > 0 %}
      {% for item in future_conferences %}  
      <div class="conference-item">  
      <p><strong>{{ item.title }}</strong></p> 
      <p><strong>Date:</strong> {{ item.date | date: "%B %d, %Y" }}</p>  
      <p><strong>Location:</strong> {{ item.location }}</p>  
      <p>{{ item.content }}  </p>
    </div>  
    {% endfor %}  
{% else %}
  <p>No upcoming conferences.</p>
{% endif %}

### Past Events 
  
{% for item in past_conferences %}  
  <div class="conference-item">  
    <p><strong>{{ item.title }}</strong></p>  
    <p><strong>Date:</strong> {{ item.date | date: "%B %d, %Y" }}</p>  
    <p><strong>Location:</strong> {{ item.location }}</p>  
    {{ item.content }}  
  </div>  
{% endfor %}
