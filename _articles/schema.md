---
weight: 0
category: Getting Started
published: true
intro: 
title: Loveland Parcel Schema
permalink: /articles/schema
layout: wider_content
---

<table>
  <thead>
    <tr>
      <th>Field</th>
      <th>Datatype</th>
      <th>Examples</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  {% for field in site.data.schema %}
    <tr>
      <td class="code">{{field[0]}}</td>
      <td class="code">{{field[1].type}}</td>
      <td>{{field[1].examples | join: ", " }}</td>
      <td>{{field[1].human}}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>