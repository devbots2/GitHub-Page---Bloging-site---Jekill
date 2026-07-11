---
layout: default
title: "DevBotS2 Blogs"
description: "Hierarchical technical documentation and articles covering Networks, Data Engineering, AI, and Robotics."
permalink: /blogs/
---

<!-- Mobile Sidebar trigger bar -->
<div class="mobile-filter-bar">
  <button class="btn-mobile-filter glass-panel" onclick="toggleMobileSidebar()">
    <svg viewBox="0 0 24 24"><path d="M3 18h18v-2H3v2zm0-5h18v-2H3v2zm0-7v2h18V6H3z"/></svg>
    Filter Categories
  </button>
</div>

<!-- Mobile Overlay -->
<div class="sidebar-overlay" id="sidebarOverlay" onclick="toggleMobileSidebar()"></div>

<!-- Full-width layout grid -->
<div class="widescreen-layout">
  
  <!-- Left Navigation Sidebar -->
  <aside class="left-sidebar-nav glass-panel" id="leftSidebarNav">
    <div class="mobile-sidebar-header">
      <h3 style="margin-bottom: 0; background: var(--gradient-brand); -webkit-background-clip: text; -webkit-text-fill-color: transparent; font-weight: 800;">Categories</h3>
      <button onclick="toggleMobileSidebar()" style="background: none; border: none; color: var(--text-primary); font-size: 1.75rem; cursor: pointer; line-height: 1;">&times;</button>
    </div>
    
    <div style="margin-bottom: 1.5rem;">
      <a href="#" class="section-link active" id="show-all-btn" onclick="resetFilter(this); event.preventDefault();" style="font-size: 1rem; font-weight: 600; padding: 0.6rem 0.75rem; border-left: 3px solid var(--color-primary); background: rgba(99, 102, 241, 0.08); display: block; border-radius: var(--radius-sm);">
        Show All Blogs
      </a>
    </div>

    <ul class="nav-tree">
      {% comment %} Get list of unique fields represented in posts {% endcomment %}
      {% assign raw_fields = "Network Engineering,Data Engineering,AI (Artificial Intelligence),Robotics,Productivity with AI - (AI as a Assistant)" | split: "," %}
      
      {% for field in raw_fields %}
        {% assign field_id = field | slugify %}
        
        <li class="nav-tree-item">
          <!-- Category Header (Clickable to Collapse) -->
          <div class="field-header" onclick="toggleCollapse('{{ field_id }}')">
            <span>{{ field }}</span>
            <svg class="field-icon" id="icon-{{ field_id }}" style="transform: rotate(180deg);" viewBox="0 0 24 24"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/></svg>
          </div>

          <!-- Collapsible content (list of languages and their sections) -->
          <div id="collapse-{{ field_id }}" class="sidebar-collapse-content" style="display: block;">
            
            <!-- English Subcategory -->
            {% assign en_posts = site.posts | where: "field", field | where: "language", "English" %}
            <div class="lang-list-container">
              <div class="lang-title" style="padding-left: 0.75rem; margin-top: 0.5rem;">
                <svg viewBox="0 0 24 24" style="width: 14px; height: 14px; fill: var(--text-secondary);"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
                <span style="font-size: 0.85rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--text-secondary); font-weight: 700;">English Blogs</span>
              </div>
              <ul class="section-list">
                {% comment %} Define standard sub-sections for English based on field {% endcomment %}
                {% if field == "Network Engineering" or field == "Data Engineering" or field == "AI (Artificial Intelligence)" or field == "Robotics" %}
                  {% assign sections = "Theory,LABs,Hands dirty with DATA Engineering,Hands dirty with AI,Hands dirty with Robotics" | split: "," %}
                {% elsif field == "Productivity with AI - (AI as a Assistant)" %}
                  {% assign sections = "Our Leanings from experience,For Kids" | split: "," %}
                {% endif %}
                
                {% for sec in sections %}
                  {% assign has_posts = site.posts | where: "field", field | where: "language", "English" | where: "section", sec %}
                  <li class="section-item">
                    <a href="#" class="section-link" id="link-{{ field_id }}-en-{{ sec | slugify }}" onclick="filterArchive('{{ field }}', 'English', '{{ sec }}', this); event.preventDefault();" style="display: flex; justify-content: space-between; align-items: center;">
                      <span>{{ sec }}</span>
                      <span style="font-size: 0.75rem; opacity: 0.6;">({{ has_posts.size }})</span>
                    </a>
                  </li>
                {% endfor %}
              </ul>
            </div>

            <!-- Sinhala Subcategory -->
            {% assign si_posts = site.posts | where: "field", field | where: "language", "Sinhala" %}
            <div class="lang-list-container" style="margin-top: 0.5rem;">
              <div class="lang-title" style="padding-left: 0.75rem;">
                <svg viewBox="0 0 24 24" style="width: 14px; height: 14px; fill: var(--text-secondary);"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
                <span style="font-size: 0.85rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--text-secondary); font-weight: 700;">Sinhala Blogs</span>
              </div>
              <ul class="section-list">
                {% comment %} Define standard sub-sections for Sinhala based on field {% endcomment %}
                {% if field == "Network Engineering" or field == "Data Engineering" or field == "AI (Artificial Intelligence)" or field == "Robotics" %}
                  {% assign sections = "Theory,LABs,Hands dirty with DATA Engineering,Hands dirty with AI,Hands dirty with Robotics" | split: "," %}
                {% elsif field == "Productivity with AI - (AI as a Assistant)" %}
                  {% assign sections = "Our Leanings from experience,For Kids" | split: "," %}
                {% endif %}
                
                {% for sec in sections %}
                  {% assign has_posts = site.posts | where: "field", field | where: "language", "Sinhala" | where: "section", sec %}
                  <li class="section-item">
                    <a href="#" class="section-link" id="link-{{ field_id }}-si-{{ sec | slugify }}" onclick="filterArchive('{{ field }}', 'Sinhala', '{{ sec }}', this); event.preventDefault();" style="display: flex; justify-content: space-between; align-items: center;">
                      <span>{{ sec }}</span>
                      <span style="font-size: 0.75rem; opacity: 0.6;">({{ has_posts.size }})</span>
                    </a>
                  </li>
                {% endfor %}
              </ul>
            </div>

          </div>
        </li>
      {% endfor %}
    </ul>
  </aside>

  <!-- Right Side Content Column -->
  <div class="main-blog-list">
    
    <!-- Filter Indicator Header -->
    <div class="glass-panel" style="padding: 1.5rem 2rem; margin-bottom: 2rem; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem;">
      <div>
        <span style="font-size: 0.8rem; text-transform: uppercase; font-weight: 700; color: var(--color-primary); letter-spacing: 0.05em;">DevBotS2 Library</span>
        <h2 id="filterHeading" style="font-size: 1.75rem; margin: 0; line-height: 1.2;">Showing All Blogs</h2>
      </div>
      <div id="postsCountBadge" class="post-category-tag" style="background: var(--gradient-brand); padding: 0.4rem 1rem; border-radius: 9999px; box-shadow: 0 4px 10px rgba(99, 102, 241, 0.2);">
        {{ site.posts.size }} Articles Available
      </div>
    </div>

    <!-- Blogs Grid list -->
    <div class="posts-grid" id="archiveGrid">
      {% for post in site.posts %}
      <article class="post-card glass-panel" 
               data-field="{{ post.field | escape }}" 
               data-language="{{ post.language | escape }}" 
               data-section="{{ post.section | escape }}"
               style="display: flex;">
        <div class="post-card-image-wrapper">
          <a href="{{ post.url | relative_url }}">
            {% if post.image %}
            <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
            {% else %}
            <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=600&q=80" alt="Placeholder">
            {% endif %}
          </a>
        </div>
        <div class="post-card-content">
          <div class="post-meta-row" style="margin-bottom: 0.5rem; flex-wrap: wrap; gap: 0.5rem;">
            {% if post.field %}
            <span class="post-category-tag" style="background: rgba(99, 102, 241, 0.1); color: var(--color-primary);">{{ post.field }}</span>
            {% endif %}
            {% if post.language %}
            <span class="post-category-tag" style="background: rgba(168, 85, 247, 0.1); color: var(--color-secondary);">{{ post.language }}</span>
            {% endif %}
            {% if post.section %}
            <span class="post-category-tag" style="background: rgba(244, 63, 94, 0.1); color: var(--color-accent);">{{ post.section }}</span>
            {% endif %}
          </div>
          <h3 class="post-card-title"><a href="{{ post.url | relative_url }}" style="color: inherit;">{{ post.title }}</a></h3>
          <p class="post-card-excerpt">{{ post.description | default: post.excerpt | strip_html | truncatewords: 20 }}</p>
          <div class="post-card-footer">
            <div class="post-card-author">
              <span>By {{ post.author | default: "DevBotS2 Team" }}</span>
            </div>
            <a href="{{ post.url | relative_url }}" class="post-card-link">
              Read Page
              <svg viewBox="0 0 24 24" style="width: 16px; height: 16px; fill: currentColor;"><path d="M12 4l-1.41 1.41L16.17 11H4v2h12.17l-5.58 5.59L12 20l8-8z"/></svg>
            </a>
          </div>
        </div>
      </article>
      {% endfor %}
    </div>

    <!-- Empty Results Container -->
    <div id="noFilterResults" class="glass-panel" style="display: none; text-align: center; padding: 5rem 2rem;">
      <svg viewBox="0 0 24 24" style="width: 64px; height: 64px; fill: var(--text-muted); margin-bottom: 1.5rem;"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-2 10H7v-2h10v2zm0-4H7V7h10v2zm0 8H7v-2h10v2z"/></svg>
      <h3 style="margin-bottom: 0.5rem; font-size: 1.5rem;">No blogs available yet</h3>
      <p style="color: var(--text-secondary); max-width: 500px; margin: 0 auto 1.5rem auto;">We haven't uploaded articles in this specific section yet. Please choose another field or write one!</p>
      <button onclick="document.getElementById('show-all-btn').click();" class="btn-read-more" style="border: none; cursor: pointer;">Go back to all blogs</button>
    </div>

  </div>
</div>

<script>
  // Dynamic sidebar section folding logic
  function toggleCollapse(id) {
    const content = document.getElementById('collapse-' + id);
    const icon = document.getElementById('icon-' + id);
    if (content) {
      if (content.style.display === 'none') {
        content.style.display = 'block';
        icon.style.transform = 'rotate(180deg)';
      } else {
        content.style.display = 'none';
        icon.style.transform = 'rotate(0deg)';
      }
    }
  }

  // Mobile Drawer Toggle
  function toggleMobileSidebar() {
    const sidebar = document.getElementById('leftSidebarNav');
    const overlay = document.getElementById('sidebarOverlay');
    sidebar.classList.toggle('active');
    overlay.classList.toggle('active');
  }

  // Core Filtering Script
  function filterArchive(field, language, section, element) {
    // 1. Remove active state from all links
    const allLinks = document.querySelectorAll('.section-link');
    allLinks.forEach(link => {
      link.classList.remove('active');
      link.style.borderLeft = 'none';
      link.style.background = 'none';
    });
    document.getElementById('show-all-btn').classList.remove('active');
    document.getElementById('show-all-btn').style.borderLeft = 'none';
    document.getElementById('show-all-btn').style.background = 'none';

    // 2. Set active styling on current link
    element.classList.add('active');
    element.style.background = 'rgba(99, 102, 241, 0.05)';
    element.style.fontWeight = '600';

    // 3. Update Title & Header values
    document.getElementById('filterHeading').innerText = field + ' > ' + language + ' > ' + section;

    // 4. Perform card filtering
    const cards = document.querySelectorAll('.post-card');
    let visibleCount = 0;

    cards.forEach(card => {
      const cardField = card.getAttribute('data-field');
      const cardLang = card.getAttribute('data-language');
      const cardSec = card.getAttribute('data-section');

      if (cardField === field && cardLang === language && cardSec === section) {
        card.style.display = 'flex';
        visibleCount++;
      } else {
        card.style.display = 'none';
      }
    });

    // 5. Update counts and empty states
    document.getElementById('postsCountBadge').innerText = visibleCount + ' Articles Shown';
    
    if (visibleCount === 0) {
      document.getElementById('archiveGrid').style.display = 'none';
      document.getElementById('noFilterResults').style.display = 'block';
    } else {
      document.getElementById('archiveGrid').style.display = 'grid';
      document.getElementById('noFilterResults').style.display = 'none';
    }

    // 6. Close mobile drawer if active
    const sidebar = document.getElementById('leftSidebarNav');
    if (sidebar.classList.contains('active')) {
      toggleMobileSidebar();
    }
  }

  // Show all posts reset
  function resetFilter(element) {
    const allLinks = document.querySelectorAll('.section-link');
    allLinks.forEach(link => {
      link.classList.remove('active');
      link.style.borderLeft = 'none';
      link.style.background = 'none';
    });

    element.classList.add('active');
    element.style.borderLeft = '3px solid var(--color-primary)';
    element.style.background = 'rgba(99, 102, 241, 0.08)';

    document.getElementById('filterHeading').innerText = 'Showing All Blogs';

    const cards = document.querySelectorAll('.post-card');
    cards.forEach(card => {
      card.style.display = 'flex';
    });

    document.getElementById('postsCountBadge').innerText = cards.length + ' Articles Available';
    document.getElementById('archiveGrid').style.display = 'grid';
    document.getElementById('noFilterResults').style.display = 'none';

    // Close mobile drawer if active
    const sidebar = document.getElementById('leftSidebarNav');
    if (sidebar.classList.contains('active')) {
      toggleMobileSidebar();
    }
  }
</script>
