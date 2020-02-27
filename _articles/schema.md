---
weight: 0
category: Getting Started
published: true
intro: 
title: The Loveland Parcel Schema
permalink: /articles/schema
layout: wider_content
---

We clean and convert all parcel data we recieve into this standard schema. Some counties may include additional fields. Wherever possible, we include those in our exports, but we do not have a key available for those fields. 

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
  {% for field in site.data.schema.schema %}
    <tr>
      <td class="code"><a name="{{field[0]}}">{{field[0]}}</a></td>
      <td class="code">{{field[1].type}}</td>
      <td>{{field[1].examples | join: ", " }}</td>
      <td>{{field[1].human}}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>
