---
layout: default
title: Home
---

# Cyber Security Study Notes

Short-form notes from my cert prep and lab work — mainly **CEH v13** and the
**8-month Full Stack Cyber & Cloud Security with AI** program.

Written for quick recall, not for reading like an article — expect bullets,
commands, and key definitions rather than long prose.

## Recent posts

<ul>
  {% for post in site.posts limit:10 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span> — {{ post.date | date: "%b %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>

## By track

- [CEH v13 notes](/ceh/)
- [Networkers Home notes](/networkers-home/)
