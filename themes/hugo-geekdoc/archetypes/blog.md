---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
author: ""
authorLink: ""
slug: "{{ substr .File.BaseFileName 11 }}"
---
