---
layout: default
title: Resume
permalink: /
---

<div class="resume-wrapper">
  <header class="resume-header">
    <h1>{{ site.data.resume.basics.name }}</h1>
    <p class="role">{{ site.data.resume.basics.label }}</p>
    <div class="contact-info">
      {% if site.data.resume.basics.email %}
        <a href="mailto:{{ site.data.resume.basics.email }}">{{ site.data.resume.basics.email }}</a>
      {% endif %}
      {% if site.data.resume.basics.phone %}
        <span> • {{ site.data.resume.basics.phone }}</span>
      {% endif %}
      {% if site.data.resume.basics.url %}
        <span> • <a href="{{ site.data.resume.basics.url }}">{{ site.data.resume.basics.url }}</a></span>
      {% endif %}
    </div>
    <div class="social-links">
      {% for profile in site.data.resume.basics.profiles %}
        <a href="{{ profile.url }}">{{ profile.network }}</a>{% unless forloop.last %} • {% endunless %}
      {% endfor %}
    </div>
  </header>

  <section class="summary section">
    <h2>Summary</h2>
    <p>{{ site.data.resume.basics.summary }}</p>
  </section>

  <section class="experience section">
    <h2>Experience</h2>
    {% for job in site.data.resume.work %}
      <div class="item">
        <div class="item-header">
          <h3>{{ job.position }}</h3>
          <span class="company">{{ job.company }}</span>
          <span class="dates">{{ job.startDate | date: "%b %Y" }} - {% if job.endDate == 'Present' %}Present{% else %}{{ job.endDate | date: "%b %Y" }}{% endif %}</span>
        </div>
        <p class="job-summary">{{ job.summary }}</p>
        <ul>
          {% for highlight in job.highlights %}
            <li>{{ highlight }}</li>
          {% endfor %}
        </ul>
      </div>
    {% endfor %}
  </section>

  <section class="skills section">
    <h2>Skills</h2>
    <div class="skills-grid">
      {% for category in site.data.resume.skills %}
        <div class="skill-category">
          <h3>{{ category.name }}</h3>
          <p>{{ category.keywords | join: ", " }}</p>
        </div>
      {% endfor %}
    </div>
  </section>

    <section class="projects section">
    <h2>Projects</h2>
    {% for project in site.data.resume.projects %}
      <div class="item">
        <div class="item-header">
          <h3>{{ project.name }}</h3>
          {% if project.url %}
             <a href="{{ project.url }}" class="project-link">[View]</a>
          {% endif %}
        </div>
        <p>{{ project.description }}</p>
        <p class="tech-stack"><em>Technologies: {{ project.keywords | join: ", " }}</em></p>
      </div>
    {% endfor %}
  </section>

  <section class="education section">
    <h2>Education</h2>
    {% for edu in site.data.resume.education %}
      <div class="item">
        <div class="item-header">
          <h3>{{ edu.institution }}</h3>
          <span class="dates">{{ edu.startDate | date: "%Y" }} - {{ edu.endDate | date: "%Y" }}</span>
        </div>
        <p>{{ edu.studyType }} in {{ edu.area }}</p>
      </div>
    {% endfor %}
  </section>

</div>
