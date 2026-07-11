---
layout: page
title: "About DevBotS2"
description: "Meet the engineering team behind the systems and insights."
permalink: /about/
---

<p style="text-align: center; max-width: 800px; margin: 0 auto 3rem auto; font-size: 1.25rem; line-height: 1.7; color: var(--text-secondary);">
  We are a team of two engineers dedicated to researching, building, and documenting systems architecture, network infrastructures, big data structures, robotics, and artificial intelligence solutions.
</p>

<!-- Double Profile Cards Layout -->
<div class="profile-cards-grid">
  {% for member in site.authors %}
  <div class="profile-card glass-panel">
    <div class="profile-card-header">
      <img src="{{ member.avatar | relative_url }}" alt="{{ member.name }}" class="profile-avatar" onerror="this.src='https://api.dicebear.com/7.x/bottts/svg?seed={{ member.name | url_encode }}'">
      <div>
        <h3 class="profile-name" style="margin-bottom: 0.25rem;">{{ member.name }}</h3>
        <div class="profile-role">{{ member.role }}</div>
      </div>
    </div>
    <div class="profile-body">
      <p>{{ member.bio }}</p>
      
      <h4 style="margin-top: 1.5rem; margin-bottom: 0.5rem; font-size: 1rem;">Primary Focus Fields</h4>
      <div style="display: flex; flex-wrap: wrap; gap: 0.5rem;">
        {% if forloop.first %}
        <span class="tag-badge" style="font-size: 0.75rem;">#NetworkEngineering</span>
        <span class="tag-badge" style="font-size: 0.75rem;">#Robotics</span>
        <span class="tag-badge" style="font-size: 0.75rem;">#AIModels</span>
        {% else %}
        <span class="tag-badge" style="font-size: 0.75rem;">#DataPipelines</span>
        <span class="tag-badge" style="font-size: 0.75rem;">#AIAssistants</span>
        <span class="tag-badge" style="font-size: 0.75rem;">#Workflows</span>
        {% endif %}
      </div>
    </div>
    <div class="profile-footer">
      <span style="font-size: 0.85rem; color: var(--text-muted);">{{ member.email }}</span>
      <div class="social-icons-row" style="gap: 0.75rem;">
        {% if member.social.github %}
        <a href="https://github.com/{{ member.social.github }}" class="social-icon-link" aria-label="GitHub" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24" style="width: 18px; height: 18px;"><path d="M12 2A10 10 0 002 12c0 4.42 2.87 8.17 6.84 9.5.5.08.66-.23.66-.5v-1.69c-2.77.6-3.36-1.34-3.36-1.34-.46-1.16-1.11-1.47-1.11-1.47-.9-.62.07-.6.07-.6 1 .07 1.53 1.03 1.53 1.03.9 1.52 2.34 1.07 2.91.83.09-.65.35-1.09.63-1.34-2.22-.25-4.55-1.11-4.55-4.92 0-1.11.38-2 1.03-2.71-.1-.25-.45-1.29.1-2.64 0 0 .84-.27 2.75 1.02.79-.22 1.65-.33 2.5-.33.85 0 1.71.11 2.5.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.35.2 2.39.1 2.64.65.71 1.03 1.6 1.03 2.71 0 3.82-2.34 4.66-4.57 4.91.36.31.69.92.69 1.85V21c0 .27.16.59.67.5C19.14 20.16 22 16.42 22 12A10 10 0 0012 2z"/></svg>
        </a>
        {% endif %}
        {% if member.social.linkedin %}
        <a href="https://linkedin.com/in/{{ member.social.linkedin }}" class="social-icon-link" aria-label="LinkedIn" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24" style="width: 18px; height: 18px;"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
        </a>
        {% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<div class="glass-panel" style="padding: 2.5rem; text-align: center; margin-top: 4rem; margin-bottom: 4rem;">
  <h3 style="margin-bottom: 1rem;">Collaborative Project Lab</h3>
  <p style="color: var(--text-secondary); margin-bottom: 1.5rem; max-width: 600px; margin-left: auto; margin-right: auto;">
    We build simulation labs and open-source data pipelines. Check our latest writings in the archive or follow us on GitHub to keep track of new releases!
  </p>
  <a href="{{ '/blogs/' | relative_url }}" class="btn-read-more">Browse Blogs</a>
</div>
