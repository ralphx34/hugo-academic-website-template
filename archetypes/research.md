+++
title = "{{ replace .File.ContentBaseName "-" " " | title }}"
authors = []
category = "working-paper"
year = {{ now.Year }}
description = ""
paper = ""
publication = ""
code = ""
data = ""
weight = 10
draft = true

[build]
  render = "never"
  list = "local"
+++