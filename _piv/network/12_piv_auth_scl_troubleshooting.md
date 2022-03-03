---
layout: page
collection: piv
title: Troubleshooting Windows Smart Card Logon with PIV Authentication 
permalink: piv/network/troubleshooting/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
    - text: Logon Process Overview
      href: '#logon-process-overview'
    - text: 1. Process Start
      href: '#1-process-start'
    - text: 2. Card Selection and PIN Entry
      href: '#2-card-selection-and-pin-entry'
    - text: 3. Credential Authentication and Secure Connection to Logon Server
      href: '#3-credential-authentication-and-secure-connection-to-logon-server'
    - text: 4. Name Mapping and PIV Validation
      href: '#4-name-mapping-and-piv-validation'
    - text: 5. Client Logon and Caching
      href: '#5-client-logon-and-caching'   
---

Within the federal enterprise, Windows smart card logon with a PIV card is the baseline capability used to satisfy Federal Information Security Management Act (FISMA) and National Institute of Standards and Technology (NIST) Risk Management Framework policy requirements regarding authentication. A PIV card enables high-assurance, two-factor authentication to a Windows desktop. Under normal conditions, this system is simple and easy for an end user to use. However, if this logon mechanism breaks, it can be difficult to troubleshoot logon and authentication errors. This page includes common symptoms and suggested steps to diagnose and solve these issues.

## Logon Process Overview

The figure below, from the “Smart card sign-in flow in Windows” section of the [Microsoft Certificate Requirements and Enumeration article](https://docs.microsoft.com/en-us/windows/security/identity-protection/smart-cards/smart-card-certificate-requirements-and-enumeration#smart-card-sign-in-flow-in-windows){:target="_blank"}{:rel="noopener noreferrer"}, provides a detailed overview of how smart card logon works in supported versions of Windows.

[![A detailed workflow diagram of how smart card logon works in supported versions of Windows.]({{site.baseurl}}/assets/piv/pivauth-overview.png)]({{site.baseurl}}/assets/piv/pivauth-overview.png){:target="_blank"}{:rel="noopener noreferrer"}

For our use, this complex process is simplified into the following workflows:
1.	[Process Start](#process-start)
2.	[Card Selection and PIN Entry](#card-selection-and-pin-entry)
3.	[Credential Authentication and Secure Connection to Logon Server](#credential-authentication-and-secure-connection-to-logon-server)
4.	[Name Mapping and PIV Validation](#name-mapping-and-piv-validation)
5.	[Client Logon and Caching](#client-logon-and-caching)

## 1. Process Start

[content here]

## 2. Card Selection and PIN Entry

[content here]

## 3. Credential Authentication and Secure Connection to Logon Server

[content here]

## 4. Name Mapping and PIV Validation

[content here]

## 5. Client Logon and Caching

[content here]
