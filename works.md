---
layout: default
title: "Works"
permalink: /works/
---

<div class="works-container">
  <h1>{{ page.title }}</h1>

  {% comment %} Added a pipe to handle the extra space in your 'Piano' category string {% endcomment %}
  {% assign categories = "Chamber, Piano, Film, Fixed Media" | split: ", " %}

  {% for category in categories %}
    {% comment %} 1. Pull, sort by year, and reverse {% endcomment %}
    {% assign category_works = site.compositions | where: "type", category | sort: "year" | reverse %}
    
    {% if category_works.size > 0 %}
      <section class="work-category">
        <h2 class="category-title">{{ category }}</h2>
        <div class="works-grid">
          {% comment %} 2. REMOVED the redundant 'where' assignment that was here {% endcomment %}
          {% for work in category_works %}
            <div class="work-item">
              <h3>
                <a href="{{ work.url | relative_url }}" class="stretched-link">
                  {{ work.title }}
                </a>
              </h3>
              <p class="work-date">{{ work.year }}</p>
            </div>
          {% endfor %}
        </div>
      </section>
    {% endif %}
  {% endfor %}
</div>