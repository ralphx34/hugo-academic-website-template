+++
title = "{{ replace .File.ContentBaseName "-" " " | title }}"
institution = ""
role = "Instructor"
term = ""
year = {{ now.Year }}
level = "Undergraduate"
coursePage = ""
syllabus = ""
materials = ""
weight = 10
draft = true

[build]
  render = "never"
  list = "local"
+++

Add an optional short description of the course or teaching responsibilities here.
