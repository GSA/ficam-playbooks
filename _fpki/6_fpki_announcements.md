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
      <th data-sortable scope="col" role="columnheader">Title</th>
      <th data-sortable scope="col" role="columnheader">Status</th>
      <th data-sortable scope="col" role="columnheader">Date</th>
      <th data-sortable scope="col" role="columnheader">Description</th>
    </tr>
  </thead>
  <tbody>
    {% assign announcements = site.fpki.announcements | concat: site.data.fpkiannouncements| sort: "status" %}
    {% for announcement in announcements %}
        <tr>
          <th scope="row"><a href="{{ announcement.url | relative_url }}">{{ announcement.title }}</a></th>
          <th scope="row">{{ announcement.status }}</th>
          <th scope="row">{{ announcement.pubDate }}</th>
          <th scope="row">{{ announcement.description }}</td>
        </tr>
    {% endfor %}
  </tbody>
</table>
