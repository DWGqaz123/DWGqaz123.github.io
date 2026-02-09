---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-01-05
type: landing

design:
  # Default section spacing
  spacing: '0'

sections:
  # Developer Hero - Gradient background with name, role, social, and CTAs
  - block: dev-hero
    id: hero
    content:
      username: me
      greeting: "Hi, I'm"
      show_status: true
      show_scroll_indicator: true
      typewriter:
        enable: true
        prefix: "I build"
        strings:
          - "full-stack Web apps"
          - "AI-driven Service"
          - "RAG System"
          - "open source tools"
        type_speed: 70
        delete_speed: 40
        pause_time: 2500
      cta_buttons:
        - text: View My Work
          url: "#projects"
          icon: arrow-down
        - text: Get In Touch
          url: "#contact"
          icon: envelope
    design:
      style: centered
      avatar_shape: circle
      animations: true
      background:
        color:
          light: "#fafafa"
          dark: "#0a0a0f"
      spacing:
        padding: ["6rem", "0", "4rem", "0"]
  
  # Filterable Portfolio - Alpine.js powered project filtering
  - block: portfolio
    id: projects
    content:
      title: "Featured Projects"
      subtitle: "A selection of my recent work"
      count: 0
      filters:
        folders:
          - projects
      buttons:
        - name: All
          tag: '*'
        - name: Full-Stack
          tag: Full-Stack
        - name: Frontend
          tag: Frontend
        - name: Backend
          tag: Backend
      default_button_index: 0
      # Archive link auto-shown if more projects exist than 'count' above
      # archive:
      #   enable: false  # Set to false to explicitly hide
      #   text: "Browse All"  # Customize text
      #   link: "/work/"  # Custom URL
    design:
      columns: 3
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Visual Tech Stack - 基于 Winston Dong 的简历
  - block: tech-stack
    id: skills
    content:
      title: "Tech Stack"
      subtitle: "Technologies I use to build AI-driven solutions"
      categories:
        - name: Languages
          items:
            - name: Python
              icon: devicon/python
            - name: Java
              icon: devicon/java
            - name: SQL
              icon: devicon/mysql
        - name: Machine Learning & AI
          items:
            - name: PyTorch 
              icon: devicon/pytorch
            - name: LangChain 
              icon: devicon/langchain
            - name: Transformers
              icon: devicon/huggingface
            - name: Gemini / OpenAI
              icon: brands/google
        - name: Backend & Data
          items:
            - name: Spring Boot
              icon: devicon/spring
            - name: PostgreSQL
              icon: devicon/postgresql
            - name: MySQL
              icon: devicon/mysql
            - name: FastAPI
              icon: devicon/fastapi
        - name: Tools & DevOps
          items:
            - name: Docker
              icon: devicon/docker
            - name: GitHub
              icon: brands/github
            - name: Jupyter
              icon: devicon/jupyter
            - name: Postman
              icon: devicon/postman
    design:
      style: grid
      show_levels: false
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
# Experience Timeline - 基于 Winston Dong 的简历
  - block: resume-experience
    id: experience
    content:
      title: Experience
      date_format: Jan 2006
      items:
        - title: AI Engineer Intern
          company: ReelFluent Inc.
          company_url: ''
          company_logo: ''
          location: Remote
          date_start: '2025-12-01'
          date_end: ''
          description: |2-
            * Developed an end-to-end LLM pipeline to extract, validate, and structure linguistic knowledge from 100k+ subtitles using Gemini API.
            * Clustered 40k+ knowledge points into 70+ product-ready "Lingo Packs" with automated metadata and SEO-ready branding[cite: 19].
            * Implemented timestamp-accurate video slicing and FFmpeg-based screenshot extraction for AI language learning[cite: 20].
            * Built an interactive AI tutor module using Flask and Gemini APIs to support real-time chat functionality[cite: 21].
            * Tech stack: Python, Gemini API, Flask, LLMs (Transformers/RAG), FFmpeg[cite: 10, 18, 21].
        - title: Testing Engineer Intern
          company: Xiaoqiang Parking (Jiahu Tech)
          company_url: ''
          company_logo: ''
          location: Hangzhou, China
          date_start: '2023-06-01'
          date_end: '2023-08-31'
          description: |2-
            * Conducted multi-concurrency stress testing (JMeter) and API connectivity tests (APIFOX) to ensure system stability[cite: 25].
            * Diagnosed slow-loading pages and login logic issues, providing critical feedback to the development team[cite: 26].
            * Led the internship team to coordinate and test CRM system integration for new parking facilities[cite: 27].
            * Tech stack: JMeter, APIFOX, Charles, Navicat, MySQL[cite: 12, 25, 27].
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Recent Blog Posts
  - block: collection
    id: blog
    content:
      title: Recent Posts
      subtitle: 'Thoughts on web development, tech, and more'
      text: ''
      filters:
        folders:
          - blog
        exclude_featured: false
      count: 3
      order: desc
    design:
      view: card
      columns: 3
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # Contact Section
  - block: contact-info
    id: contact
    content:
      title: Get In Touch
      subtitle: "Let's build something amazing together"
      text: |-
        I'm always interested in hearing about new projects and opportunities.
        Whether you're looking to hire, collaborate, or just want to say hi, feel free to reach out!
      email: wenguand@andrew.cmu.edu
      autolink: true
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]
  
  # CTA Card
  - block: cta-card
    content:
      title: "Open to Opportunities"
      text: |-
        I'm currently looking for **AI Engineer/ML Engineer** or **Software Developer** roles.
        
        Let's connect and discuss how I can help your team.
      button:
        text: 'Download Resume'
        url: uploads/resume.pdf
        new_tab: true
    design:
      card:
        # Light mode: soft pastel theme gradient | Dark mode: rich deep gradient
        css_class: 'bg-gradient-to-br from-primary-200 via-primary-100 to-secondary-200 dark:from-primary-600 dark:via-primary-700 dark:to-secondary-700'
        text_color: dark
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "6rem", "0"]
---
