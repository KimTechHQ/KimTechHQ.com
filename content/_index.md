---
# Leave the homepage title empty to use the site title
title: ''
date: 2025-10-02
type: landing

design:
  # Default section spacing
  spacing: '6rem'

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download Resume
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      # Apply a gradient background
      css_class: hbx-bg-gradient
      # Avatar customization
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: markdown
    content:
      title: '💡 Mission Statement'
      subtitle: ''
      text: |-
        Committed to building a future where technological progress is matched by fairness, accessibility, and responsible policy. My mission is to grow as a professional who contributes not just to innovation itself, but to ensuring that its benefits are equitably distributed across society.

        Please reach out to collaborate 🤝
  - block: collection
    id: news
    content:
      title: Discover More
      subtitle: ''
      text: ''
      # Page type to display. E.g. post, talk, publication...
    page_type: [project]
    
---
