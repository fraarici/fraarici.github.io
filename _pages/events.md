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
      <p>
        <strong>
          {% if item.end_date %}
            {{ item.date | date: "%B %d" }} – {{ item.end_date | date: "%B %d, %Y" }}
          {% else %}
            {{ item.date | date: "%B %d, %Y" }}
          {% endif %}
        </strong>. <em>{{ item.title }}</em>
      </p> 
      <p><strong>Location:</strong> {{ item.location }}</p> 
  </div>  
    {% endfor %}  
{% else %}
  <p>No upcoming conferences.</p>
{% endif %}

### Recent Past Events 
  
{% for item in past_conferences %}  
  <div class="conference-item">  
    <p>
      <strong>
        {% if item.end_date %}
          {{ item.date | date: "%B %d" }} – {{ item.end_date | date: "%B %d, %Y" }}
        {% else %}
          {{ item.date | date: "%B %d, %Y" }}
        {% endif %}
      </strong>. <em>{{ item.title }}</em>
    </p> 
    <p><strong>Location:</strong> {{ item.location }}</p> 
    {{item.content}}
  </div>  
{% endfor %}
