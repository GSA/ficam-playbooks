---
layout: page
collection: fpki
title: Path Discovery and Validation
permalink: fpki/pdval/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: What is PDVAL?
    href: '#what-is-pdval'
  - text: How are Paths Built?
    href: '#how-are-paths-built'
  - text: What certificate fields impact path building?
    href: '#what-certificate-fields-impact-path-building'
  - text: What is Revocation Checking?
    href: '#what-is-revocation-checking'
    
---

## What is PDVAL
A process to verify the binding of a public key to a certificate subject by conducting several checks to include integrity/signature validation, usage, validity

## How are Paths Built
subject/issuer name matching, SKI/AKI matching, 

## What Certificate Fields Impact Path Building
Date processing/validity periods, path constraints, policy constrints, etc.

## What is Revocation Checking
outline how CRLs and OCSP work at a high level
