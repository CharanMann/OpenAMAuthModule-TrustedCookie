# OpenAMAuthModule-TrustedCookie

*An OpenAM Custom Authentication Module using Trusted Cookies*


This custom authentication module can be used to perform SSO across 3rd party WAM (Web Access Management) product and OpenAM using trusted HTTP cookies
For simplicity; this 3rd party WAM shall be referred as SampleVendor WAM in this document.  

Disclaimer of Liability :
=========================
The code for this project is only meant for DEMO purposes only and is not PRODUCTION ready. This is a sample implementation only and is not supported by ForgeRock. 
I make no warranty, representation or undertaking whether expressed or implied, nor does it assume any legal liability, whether direct or indirect, or responsibility for the accuracy, 
completeness, or usefulness of any information. 

Further analysis on the detailed requirements, fine-tuning and validation of the proposed architecture is still required by the selected Systems Integrator and/or Architects in charge of 
architecting the IAM project.

Pre-requisites :
================
1. SampleVendor WAM has been deployed and configured.
2. OpenAM has been deployed and configured. 
    

OpenAM Configuration:
=====================
1. Build the custom auth module by using maven. 
2. Deploy the custom auth module. Refer instructions: *[Building and Installing Custom Authentication Modules](http://openam.forgerock.org/doc/bootstrap/dev-guide/index.html#build-config-sample-auth-module)*
3. Configure the custom auth module. Refer instructions: *[Configuring and Testing Custom Authentication Modules](https://forgerock.org/openam/doc/bootstrap/dev-guide/index.html#configuring-testing-sample-auth-module)*
 
Testing:
========
1. Navigate to SampleVendor WAM login page and perform authentication. After successful authentication, SampleVendor WAM sets the trusted WAM's SSO cookie. 
2. Navigate to resource protected by OpenAM. OpenAM performs authentication using trusted cookie authentication module. In actual deployment OpenAM custom authentication module should invoke SampleVendor WAM's
API for cookie validation. OpenAM should allow access to protected resource (if OpenAM authorization policy evaluation succeeds). 
 
Curl command(s):
- curl -X POST -H "Content-Type: application/json" --cookie "X-Special-Trusted-User=demo" "http://openam13.sample.com:8080/openam/json/authenticate" -v

* * *

The contents of this file are subject to the terms of the Common Development and
Distribution License (the License). You may not use this file except in compliance with the
License.

You can obtain a copy of the License at legal/CDDLv1.0.txt. See the License for the
specific language governing permission and limitations under the License.

When distributing Covered Software, include this CDDL Header Notice in each file and include
the License file at legal/CDDLv1.0.txt. If applicable, add the following below the CDDL
Header, with the fields enclosed by brackets [] replaced by your own identifying
information: "Portions copyright [year] [name of copyright owner]".

Copyright 2016 Charan Mann

Portions Copyrighted 2016 ForgeRock AS
