---
creation date: <% tp.file.creation_date() %>
tags: Journal <% tp.file.title.split('-')[0] %>
---

modification date: *<%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") +%>*

# Journal for <% tp.file.title %>

<< [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>]]>>

