---
layout: page
collection: fpki
title: Announcements
permalink: fpki/announcements/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: Active
    href: ../announcements/test-tools/
  - text: Archived
    href: ../announcements/2019fpkimigration/
---

These announcements and hot topic concern Federal Public Key Infrastructure changes that may affect your agency's operations. Announcements are archived after one year and removed after three years.

<table class="usa-table--borderless announce-table">
  <thead class="usa-sr-only">
    <tr>
      <th id="announce-table-heading-title" scope="col">Title</th>
      <th id="announce-table-heading-status" scope="col">Status</th>
      <th id="announce-table-heading-date" scope="col">Date</th>
      <th id="announce-table-heading-description" scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    {% assign announcements = site.fpki.announcements | concat: site.data.fpkiannouncements| sort: "status" %}
    {% for announcement in announcements %}
        <tr class="announce-table-row">
          <td><a href="{{ announcement.url | relative_url }}">{{ announcement.title }}</a></td>
          <td>{{ announcement.status }}</td>
          <td>{{ announcement.pubDate }}</td>
          <td>{{ announcement.description }}</td>
        </tr>
    {% endfor %}
  </tbody>
</table>
