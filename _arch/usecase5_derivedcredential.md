---
layout: page
title: 5. Issue a Derived Credential
collection: arch
permalink: /arch/derivecredential/
sidenav: archusecases
sticky_sidenav: true
---

[![Three hexagons with the letters I, C, and A. The C is highlighted in green for Credential Management, with a green banner for the Maintenance service.](../../assets/arch/usecases/Credential-Maintenance.png){:align="right" style="padding-left:15px"}](../../assets/arch/usecases/Credential-Maintenance.png){:target="_blank"}{:rel="noopener noreferrer"}

A derived credential is a credential derived from an existing credential, with a different form factor, such as a credential on a mobile device. Derived credentials have the same IAL as the existing credential and the same or lower AAL.

When an employee or contractor requires authentication but cannot leverage an existing credential, they can use a derived credential. To be eligible for a derived credential, the employee or contractor must already have a valid credential with Authenticator Assurance Level (AAL) 2 or 3.

---

## Use Case

In this use case, an employee or contractor interacts with the agency services to register or request a derived credential. 

[![Icon Key for the diagrams that follow.](../../assets/arch/usecases/5-IconKey.png)](../../assets/arch/usecases/5-IconKey.png){:target="_blank"}{:rel="noopener noreferrer"}

<style>

td {
  font-family: "Cambria", "Georgia", "Times New Roman", "Times", serif;
  vertical-align:top;
}

</style>

<table>
  <tr>
    <td style="width:250px;border:0px;"><strong>1. Initiate the request</strong> <br> <a href="../../assets/arch/usecases/5-1.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/arch/usecases/5-1.png" width="250" alt="A diagram showing an employee or contractor initiating a derived credential request to an enterprise identity management system."></a></td>
    <td style="border:0px;">A request for identity data is initiated to the identity manager. <br><br><i> This identity manager could be a person or system, depending on the organization.</i></td>
  </tr>
  <tr>
    <td style="width:250px;border:0px;"><strong>2. Authenticate the existing credential</strong> <br> <a href="../../assets/arch/usecases/5-2.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/arch/usecases/5-2.png" width="250" alt="A diagram showing an employee or contractor authenticating an existing credential to an enterprise identity management system."></a></td>
    <td style="border:0px;">The identity manager identifies relevant sources of data on the individual. <br><br><i> Sources could include HR systems, security data, and personal databases.</i></td>
  </tr>
    <tr>
    <td style="width:250px;border:0px;"><strong>3. Generate the derived credential</strong> <br> <a href="../../assets/arch/usecases/5-3.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/arch/usecases/5-3.png" width="250" alt="A diagram showing an enterprise identity management system generating a derived credential for an employee or contracter."></a></td>
    <td style="border:0px;">Generate the derived authenticator and note the change in the user's enterprise identity record.</td>
  </tr>
</table>

## Examples

- I want to provide an employee or contractor, who has already been issued an enterprise credential, a derived credential so that they can authenticate to enterprise applications.
- An employee or contractor travels quite a bit as part of their job.  Accordingly, they are frequently limited to using a small tablet or their phone to stay connected while on the go. In this case, a derived credential is needed for purposes such as accessing secure agency websites or an agency VPN from their mobile device.
