---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Integrate your software with Common Transit Convention Traders API.
---

# CTC Traders API phase 5 testing guide

## Useful CTC Page Links
[CTC Traders API roadmap](/roadmaps/common-transit-convention-traders-roadmap/#phase-5)

[CTC Traders API specification](/api-documentation/docs/api/service/common-transit-convention-traders/2.0)

[CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/)

## Introduction

This guidance page signposts software developers to essential information and materials.

This is needed when testing to check your software is compatible and will work with our CTC Traders API.

Scroll down the page for further instructions.

##Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/).

We strongly advise you to start testing your software for compatibility purposes as soon as possible.

## What is Trader Test?

Trader Test simulates automated responses. It also provides an environment in which New Computerised Transit System (NCTS) support staff simulate the tasks done by Border Force personnel.

Trader Test enables you to check that your software is fully compatible with the CTC Traders API. Using Trader Test to validate the compatibility of your software is a prerequisite to being given access to the live production environment.

Phase 5 Trader Test is currently unavailable pending ongoing work to complete the phase 5 test scenarios. 

## What is the Test Support API?

The Test Support API enables you to inject transit movement notifications as if they have been sent by NCTS from an office of departure or an office of destination. Until automated responses to trader messages are supported in a Trader Test environment, the Test Support API enables responses to be triggered manually. 

**Note:** The Test Support API is not a substitute for Trader Test. It will be switched off as soon as Trader Test becomes available.

You must make requests to the Test Support API in JSON format. The Test Support API injects messages in XML format.

For more information, see [CTC Traders Test Support API specification](/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0).

## Get set up for testing

1. First **register** for a developer account. You can do this by following the instructions on the [Using the Developer Hub](/api-documentation/docs/using-the-hub) page.
2. [**Sign back in**](/developer/login) to the HMRC Developer Hub.
3. **Create an application** by going to the Create Test User API.
4. Then **create another application** by going to the [Common Transit Convention Traders API](/api-documentation/docs/api/service/common-transit-convention-traders/1.0).
5. **Create a user ID and password** for either an [individual](/api-documentation/docs/api/service/api-platform-test-user/1.0#_create-a-test-user-which-is-an-individual_post_accordion) or an [organisation](/api-documentation/docs/api/service/api-platform-test-user/1.0#_create-a-test-user-which-is-an-organisation_post_accordion).
6. **Subscribe to our Common Transit Convention Traders API** on the Developer Hub under the section 'Your Specific Applications'.
7. **Create a Client ID and Client Secret.**
8. Use the [Create Test User API](/api-documentation/docs/api/service/api-platform-test-user/1.0) to **generate a new test user**. Ensure that the test user has the correct enrolment by including the following request body in the call to the Create Test User API:

    ```json
    {   
        "serviceNames": [     
            "common-transit-convention-traders"   
        ] 
    }
    ```

## Get support

### General support for development and testing

Email our Software Developer Support Team at [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk) if you have any questions or difficulties or need additional clarification on this testing process. 

### Finding a bug

If you have found a bug in our code, you can get in touch with our developers directly on our [Github issues page](https://github.com/hmrc/common-transit-convention-traders/issues).

##Useful CTC page links

[CTC Traders API roadmap](/roadmaps/common-transit-convention-traders-roadmap/#phase-5)

[CTC Traders API specification](/api-documentation/docs/api/service/common-transit-convention-traders/2.0)

[CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/)
