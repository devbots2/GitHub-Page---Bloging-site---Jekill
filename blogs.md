---
layout: page
title: "Blogs Archive"
description: "Chronological archive of all articles, categorized for easy navigation."
permalink: /blogs/
---

<!-- Category Filter Tabs -->
<div style="display: flex; gap: 0.75rem; flex-wrap: wrap; margin-bottom: 3rem; justify-content: center;">
  <button class="tag-badge active-category-btn" onclick="filterCategory('all')" id="cat-all" style="cursor: pointer; padding: 0.4rem 1.2rem; font-weight: 600;">All Posts</button>
  {% assign categories = "" | split: "," %}
  {% for post in site.posts %}
    {% for category in post.categories %}
      {% unless categories contains category %}
        {% assign categories = categories | push: category %}
      {% endunless %}
    {% endfor %}
  {% endfor %}
  
  {% for category in categories %}
  <button class="tag-badge" onclick="filterCategory('{{ category }}')" id="cat-{{ category }}" style="cursor: pointer; padding: 0.4rem 1.2rem; font-weight: 600;">{{ category | capitalize }}</button>
  {% endfor %}
</div>

<!-- Chronological Posts List -->
<div class="archive-list" style="display: flex; flex-direction: column; gap: 1.5rem; max-width: 800px; margin: 0 auto 4rem auto;">
  {% for post in site.posts %}
  <div class="archive-item glass-panel" data-categories="{{ post.categories | join: ',' }}" style="padding: 1.5rem 2rem; display: flex; justify-content: space-between; align-items: center; gap: 2rem; transition: transform var(--transition-fast), border-color var(--transition-fast);">
    <div>
      <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 0.5rem; font-size: 0.85rem; color: var(--text-muted);">
        <span>{{ post.date | date: "%B %d, %Y" }}</span>
        {% if post.categories.size > 0 %}
        <span class="post-category-tag" style="background: rgba(var(--color-primary-rgb), 0.1); color: var(--color-primary); padding: 0.1rem 0.5rem; border-radius: 4px; font-weight: 600; font-size: 0.7rem; text-transform: uppercase;">{{ post.categories[0] }}</span>
        {% endif %}
      </div>
      <h3 style="font-size: 1.25rem; margin-bottom: 0.25rem;"><a href="{{ post.url | relative_url }}" style="color: inherit;">{{ post.title }}</a></h3>
      <p style="color: var(--text-secondary); font-size: 0.95rem; line-height: 1.4;">{{ post.description | default: post.excerpt | strip_html | truncatewords: 15 }}</p>
    </div>
    <a href="{{ post.url | relative_url }}" class="btn-read-more" style="padding: 0.5rem 1rem; border-radius: var(--radius-sm); font-size: 0.85rem; flex-shrink: 0; box-shadow: none;">
      Read
    </a>
  </div>
  {% endfor %}
</div>

<!-- Style for active category filter state -->
<style>
  .tag-badge.active-category-btn {
    background: var(--gradient-brand);
    color: #fff;
    border-color: transparent;
  }
</style>

<!-- Category Filtering Script -->
<script>
  function filterCategory(category) {
    // Update button styling
    const buttons = document.querySelectorAll('button[id^="cat-"]');
    buttons.forEach(btn => {
      btn.classList.remove('active-category-btn');
    });
    
    const activeBtn = document.getElementById('cat-' + category);
    if (activeBtn) {
      activeBtn.classList.add('active-category-btn');
    }
    
    // Filter posts
    const items = document.querySelectorAll('.archive-item');
    items.forEach(item => {
      if (category === 'all') {
        item.style.display = 'flex';
      } else {
        const itemCats = item.getAttribute('data-categories') || '';
        const catArray = itemCats.split(',');
        if (catArray.includes(category)) {
          item.style.display = 'flex';
        } else {
          item.style.display = 'none';
        }
      }
    });
  }
</script>
