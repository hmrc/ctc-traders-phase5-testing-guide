---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Verify the compatibility of your software with CTC Traders API and learn how to test your application in our sandbox environment.
---

# CTC Traders API phase 5 testing guide

Learn how to test the compatibility of your software with [CTC Traders API v2.0](/api-documentation/docs/api/service/common-transit-convention-traders/2.0).

## Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/) and [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/) if you have not already done so.

### Testing cycles

As part of ensuring your readiness for the go-live of phase 5 of the New Computerised Transit System (NCTS5) in November 2023, you will have to complete at least two testing cycles during 2023.

| Cycle         | Description                                                  | Scope                                                        | Message fields         |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------- |
| Assurance     | Before NCTS5 goes live, you will need to check that your software is compatible with CTC Traders API v2.0. This involves using predefined test scenarios and test data. | Small messages (up to 5MB)                                   | Mandatory and optional |
|               | You have the option to send large messages to the NCTS. Large message tests are based on the same test scenarios as small message tests.<br /><br />**Note:** The large messages functionality of CTC Traders API v2.0 will be available soon. | Large messages (5MB to 22MB                                  | Mandatory and optional |
| Accreditation | Applying for production credentials for this API will involve submitting the following:<ul><li>a completed application form to our [Software Developer Support (SDS) Team](mailto:SDSTeam@hmrc.gov.uk)</li><li>test results that are less than 14 days old</li></ul><br />**Note:** You will need to submit these items by 13 October 2023 if you want to have production credentials for the API before NCTS5 goes live on 16 November. | Small messages <br /><br />Large messages (if applicable)<br /><br />Transition rules? | Mandatory only         |

If you intend to use [CTC Guarantee Balance API v2.0](/api-documentation/docs/api/service/common-transit-convention-guarantee-balance/2.0), your NCTS5 assurance and accreditation testing will also need to include testing the compatibility of your software with that API. For more information, see CTC Guarantee Balance API phase 5 testing guide (pending).

We strongly advise you to start testing the compatibility of your software as soon as possible.

### Test environments

You must use our sandbox environment and Trader Test to test the compatibility of your software with CTC Traders API v2.0.

#### Sandbox environment

Use our sandbox environment to perform a series of compatibility tests on your software. This is a replica of the live production environment. You’ll also need to make use of some sample scenarios and test data for both Great Britain and Northern Ireland.

#### Test Support API

[CTC Traders Test Support API v2.0](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0) enables you to inject transit movement notifications as if they have been sent by the NCTS from a customs office of departure or destination. Until automated responses to trader messages are supported in a Trader Test environment, the API enables responses to be triggered manually. 

**Note:** The CTC Traders Test Support API is not a substitute for Trader Test. It will be switched off as soon as Trader Test becomes available.

You must make requests to the CTC Traders Test Support API in JSON format. The API injects messages in XML format.

For more information, see [CTC Traders Test Support API v2.0 reference](/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0/oas/page).

#### Trader Test

Trader Test is a test environment that simulates both automated responses and real-life experience where NCTS support staff do the tasks of Border Force personnel. When your testing requires a manual response, NCTS support staff will perform the live manual steps of the process. This simulates and tests a full real-life journey from start to finish for you.

### Testing prerequisites

For information about actions that must be completed before testing, see the getting started section of the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/#getting-started).

### Testing scope

???

### Transition period

After NCTS5 goes live in November 2023, there will be a transition period during which:

- the NCTS4 service will continue running only to deal with in-flight transit declarations submitted before the go-live date
- the NCTS5 service will handle all new transit declarations submitted from the go-live date onwards

During the transition period, any business ([Rules B](/guides/ctc-traders-phase5-tis/documentation/rules-b.html)) and technical ([Rules E](/guides/ctc-traders-phase5-tis/documentation/rules-e.html)) rules with Transitional Period (TP) measures defined in the [NCTS Phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/) will be applied to:

- all electronic customs clearance (ECC) messages exchanged among national customs administrations of CTC member countries and with European Commission

- the following ECC message types exchanged between traders and customs offices:

- - 'Arrival Notification' E_ARR_NOT (IE007)
  - 'Declaration Amendment' E_DEC_AMD (IE013)
  - 'Declaration Data' E_DEC_DAT (IE015)
  - 'Presentation Notification For The Pre-Lodged Declaration' E_PRE_NOT (IE170)

As part of your assurance and accreditation testing for NCTS5 you will need to run some tests to verify how your software handles transition rules.

## Related documentation

- [CTC Traders API roadmap](/roadmaps/common-transit-convention-traders-roadmap/)
- [CTC Traders API v2.0 reference](/api-documentation/docs/api/service/common-transit-convention-traders/2.0/oas/page)
- [CTC Traders API v2.0 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.0-changelog) (GitHub)
- [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/)
- CTC Guarantee Balance API phase 5 testing guide (pending)
- [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/)
- [NCTS phase 4-phase 5 data mapping spreadsheet](https://github.com/hmrc/ctc-traders-phase5-tis/blob/main/source/figures/NCTS-P5_Datamapping_R3_140323_v1.0.xlsx) (GitHub)
- [Transit Manual Supplement](https://www.gov.uk/government/publications/transit-manual-supplement) - UK transit procedures (OpenDocument Text document)

## Getting help and support

Before contacting us, find out if there is planned API downtime or a technical issue by checking [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk/?_ga=2.139406967.536493967.1674469117-2060941422.1667396839) and [New Computerised Transit System service availability](https://www.gov.uk/guidance/new-computerised-transit-system-service-availability?_ga=2.174532070.536493967.1674469117-2060941422.1667396839).

If you have specific questions about the CTC Traders API, contact our Software Developer Support (SDS) Team. You’ll get an initial response within 2 working days.

You can also email questions to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk). We might ask for more detailed information when we respond.

## Changelog

You can find the changelog for this document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.
