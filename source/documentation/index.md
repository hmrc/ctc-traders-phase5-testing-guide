---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Verify the compatibility of your software with CTC Traders API and learn how to test your application in our sandbox environment.
---

# CTC Traders API phase 5 testing guide

Learn how to test the compatibility of your software with New Computerised Transit System phase 5 (NCTS5) and  [CTC Traders API v2.0](/api-documentation/docs/api/service/common-transit-convention-traders/2.0).

**Important:** This document will be updated as we add more functionality to the NCTS5 Trader Test environment. To learn about changes to the document as we publish them, you should monitor the changelog for the document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.

## Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/) and [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/) if you have not already done so. It is also advisable to review the [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R3_140323_v1.0.xlsx) (GitHub) so that you understand differences in message types between NCTS4 and NCTS5.

### Testing cycles

As part of ensuring your readiness for the go-live of NCTS5 on 16 November 2023, you will have to complete at least two testing cycles prior to this.

| Cycle | Description | Scope | Message fields |
| ----- | ----------- | ----- | -------------- |
| Assurance | Before NCTS5 goes live, you will need to check that your software is compatible with both it and CTC Traders API v2.0. This involves using predefined test scenarios and test data. | Small messages (up to 5MB) | Mandatory and optional |
| | You have the option to send large messages to NCTS. Large message tests are based on the same test scenarios as small message tests. | Large messages (up to 5MB - this limit will later increase to 8MB) | Mandatory and optional |
| Accreditation (deferred - see note below) | Applying for production credentials for this API will involve submitting the following:<ul><li>a completed application form to our [Software Developer Support (SDS) Team](mailto:SDSTeam@hmrc.gov.uk)</li><li>test results that are less than 14 days old</li></ul><br />**Note:** You will need to submit these items by 13 October 2023 if you want to have production credentials for the API before day 1 of NCTS5 go-live. | Small messages <br /><br />Large messages (if applicable)<br /><br />Transition rules (requirements not yet finalised) | Mandatory only |

**Important:** Although it is currently possible to carry out assurance testing in NCTS5 Trader Test, accreditation testing in Trader Test will not be possible until later in 2023. This is because the functionality of Trader Test will be delivered incrementally, including the ability to test NCTS5 transition rules.

If you intend to use [CTC Guarantee Balance API v2.0](/api-documentation/docs/api/service/common-transit-convention-guarantee-balance/2.0), your NCTS5 assurance and accreditation testing will also need to include testing the compatibility of your software with that API. For more information, see CTC Guarantee Balance API phase 5 testing guide (pending).

We strongly advise you to start testing the compatibility of your software as soon as possible.

**Note:** At this time, please restrict your testing to the test scenarios in this document. HMRC cannot support tests that are not included here.

### Test environments

You must use our sandbox environment and Trader Test to test the compatibility of your software with CTC Traders API v2.0.

#### Test Support API

[CTC Traders Test Support API v2.0](/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0) enables you to inject transit movement notifications as if they have been sent by the NCTS from a customs office of departure or destination.

You must make requests to the CTC Traders Test Support API in JSON format. The API injects messages in XML format.

For more information, see [CTC Traders Test Support API v2.0 reference](/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0/oas/page).

#### Trader Test

Trader Test is a test environment that simulates both automated responses and real-life experience where NCTS support staff do the tasks of Border Force personnel. When your testing requires a manual response, NCTS support staff will perform the live manual steps of the process. This simulates and tests a full real-life journey from start to finish for you.

**Note:** Currently, you can use NCTS5 Trader Test to test only small messages (up to 5MB in size) with departures process flows (as defined in this document). We will advise when arrivals, incidents, and pre-lodgements process flows are testable.

##### Accessing Trader Test

Before requesting access to NCTS5 Trader Test, note the following:

- you have the option to use both Trader Test and the Test Support API for your assurance testing (but only Trader Test can be used for accreditation testing)
- you need to continue using the Test Support API if you want to continue testing a broad range of message types as we add more functionality to Trader Test
- an application with its Client ID registered for Trader Test should not use the Test Support API
- if you want to use to both Trader Test and the Test Support API, you must set up two different applications in the sandbox environment because you will need two different Client IDs
- access is to Trader Test is based on an allow list

To request access to NCTS5 Trader Test, complete the following steps:
1. You must email your access request to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk).
2. In the email, you must provide the Client ID of the application that you want to use with Trader Test, and you cannot subsequently use that Client ID with the Test Support API.

### Testing prerequisites

For information about actions that must be completed before testing, see the getting started section of the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/#getting-started).

### Message sizes

CTC Traders API v2.0 supports both small (up to 5MB in size) and large (up to 5MB in size - this limit will later increase to 8MB) messages.

**Note:** The 5MB limit for large messages is testable in NCTS5 Trader Test. We will advise you when the 8MB limit becomes testable in Trader Test.

### UK cutover from NCTS4 to NCTS5

After NCTS5 goes live on 16 November 2023, there will be a cutover period during which:

- the NCTS4 service will continue running only to deal with in-flight transit declarations submitted before the go-live date
- the NCTS5 service will handle all new transit declarations submitted from the go-live date onwards

### Transition period

The transition period is the period of time during which countries may switch to operating NCTS5 at any point and will run until all countries have switched to operating NCTS5. NCTS operations are currently considered to be in the transition period.

During the transition period, those countries that are operating NCTS5 must do so in transitional mode, which is equivalent to a 'backwards compatibility' mode. This is to ensure that messages can be exchanged between NCTS4 and NCTS5 countries, which is handled by an upgrade/downgrade convertor in the common domain, where messages are exchanged at country to country level. For example, notifying the country of destination that the movement has been released or notifying the country of departure that the movement has arrived, and so on.

The UK’s NCTS5 service will go live during the transition period. 

To ensure backwards compatibility with NCTS4 during transition, special rules and conditions have been defined to restrict/prevent usage of new data fields and some functionality until all countries are operating NCTS5. This allows downgrading of NCTS5 messages to NCTS4.

The prefixes of these rules and conditions are as follows.

| Rule prefix | Description |
| ----------- | ----------- |
| B | Restrictive business rules effective during transitional period. |
| E | Restrictive technical rules effective during transitional period. |

During the transition period, NCTS will observe and apply these business ([Rules B](/guides/ctc-traders-phase5-tis/documentation/rules-b.html)) and technical ([Rules E](/guides/ctc-traders-phase5-tis/documentation/rules-e.html)) rules as defined in the [NCTS Phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/).

As part of your assurance and accreditation testing for NCTS5, you will need to run some predefined tests to verify how your software handles transition rules.

**Note:** It is not currently possible to carry out transition rules testing in NCTS5 Trader Test. There will be transition rules testing windows before and during the accreditation testing window. We will advise you about those testing windows nearer the time.

## Related documentation

- [CTC Traders API roadmap](/roadmaps/common-transit-convention-traders-roadmap/)
- [CTC Traders API v2.0 reference](/api-documentation/docs/api/service/common-transit-convention-traders/2.0/oas/page)
- [CTC Traders API v2.0 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.0-changelog) (GitHub)
- [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/)
- CTC Guarantee Balance API phase 5 testing guide (pending)
- [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/)
- [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R3_140323_v1.0.xlsx) (GitHub)
- [Transit Manual Supplement](https://www.gov.uk/government/publications/transit-manual-supplement) - UK transit procedures (OpenDocument Text document)

## Getting help and support

Before contacting us, find out if there is planned API downtime or a technical issue by checking [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk) and [New Computerised Transit System service availability](https://www.gov.uk/guidance/new-computerised-transit-system-service-availability).

If you have specific questions about the CTC Traders API, contact our Software Developer Support (SDS) Team. You’ll get an initial response within 2 working days.

You can also email questions to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk). We might ask for more detailed information when we respond.

## Changelog

You can find the changelog for this document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.
