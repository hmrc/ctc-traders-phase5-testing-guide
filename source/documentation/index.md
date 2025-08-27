---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Verify the compatibility of your software with CTC Traders API and learn how to test your application in our sandbox environment.
---

# CTC Traders API phase 5 testing guide

Learn how to test the compatibility of your software with New Computerised Transit System phase 5 (NCTS5) and [CTC Traders API v2.1](/api-documentation/docs/api/service/common-transit-convention-traders/2.1).

[Learn about key NCTS5 dates](/guides/ctc-traders-phase5-tis/#ncts5-key-dates).

**Note:** Please restrict your testing to the test scenarios in this document. HMRC cannot support tests that are not included here.

## Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/) and [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/) if you have not already done so. It is also advisable to review the [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R5_111023_v1.0.xlsx) so that you understand differences in message types between NCTS4 and NCTS5.

### Testing cycles

As part of ensuring your readiness for go-live of the UK NCTS5 final state, you will have to complete the assurance testing

| Cycle                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Start date      | End date      | Scope                                                                                 | Message fields         |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|---------------------------------------------------------------------------------------|------------------------|
| Assurance                    | Before go-live, you will need to check that your software is compatible with both it and CTC Traders API v2.1. This involves using predefined test scenarios and test data.                                                                                                                                                                                                                                                                                                                                                                                            |                 |               | Small messages (up to 5MB)                                                            | Mandatory and optional |
|                              | You have the option to send large messages to NCTS. Large message tests are based on the same test scenarios as small message tests.                                                                                                                                                                                                                                                                                                                                                                                                                                   |                 |               | Large messages (up to 8MB)                                                            | Mandatory and optional |

**Please note**: CTC Traders API v2.0 will no longer be operational from 21 January 2025. All existing users must upgrade to CTC Traders API v2.1 for submitting declarations.

If you intend to use [CTC Guarantee Balance API v2.0](/api-documentation/docs/api/service/common-transit-convention-guarantee-balance/2.0):

- your NCTS5 assurance testing will also need to include testing the compatibility of your software with that API - for more information, see [CTC Guarantee Balance API phase 5 testing guide](/guides/ctc-guarantee-balance-phase5-testing-guide/)
- you do NOT have to apply for separate production credentials for that API - this is because production credentials for CTC Traders API v2.0 are sufficient for using the UK NCTS5 service after it goes live

### Test environments

You must use our sandbox environment and Trader Test to test the compatibility of your software with CTC Traders API v2.1.

#### Trader Test

Trader Test is a test environment that simulates both automated responses and real-life experience where NCTS support staff do the tasks of Border Force personnel. When your testing requires a manual response, NCTS support staff will perform the live manual steps of the process. This simulates and tests a full real-life journey from start to finish for you.

You can use NCTS5 Trader Test to test small messages (up to 5MB in size) and large messages (up to 8MB in size) with standard departures process flows, pre-lodged departures process flows, and arrivals process flows (as defined in this document).

**Note:** If you have an HMRC [developer account](/developer/login) and can access our sandbox environment, you have access to the NCTS5 Trader Test environment automatically.

### Testing prerequisites

For information about actions that must be completed before testing, see the getting started section of the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/#getting-started).

### Message sizes

CTC Traders API v2.1 supports both small (up to 5MB in size) and large (up to 8MB in size) messages. Both message sizes are testable in Trader Test.

## Navigating CTC Traders API v2.1 documentation

The following table lists the documents for CTC Traders API v2.1 and outlines the content and intended readers of each document.

<table>
    <thead>
        <tr>
            <th>Document</th>
            <th>Content type</th>
            <th>Granularity</th>
            <th>Summary</th>
            <th>Intended readers</th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <td><a href="https://developer.service.hmrc.gov.uk/roadmaps/common-transit-convention-traders-roadmap/">CTC Traders API roadmap</a> (covers NCTS4 onwards)</td>
            <td>Functional</td>
            <td>High level</td>
            <td><p>Outlines current status of API for each NCTS phase</p><p>Outlines any development plans for API</p></td>
            <td><p>Software developers</p> <p>Technical architects </p> <p>Product managers</p> <p>Business analysts</p></td>
        </tr>
        <tr>
            <td><a href="https://developer.service.hmrc.gov.uk/guides/ctc-traders-phase5-tis/">NCTS phase 5 technical interface specification</a> (TIS)</td>
            <td>Technical (business logic/rules)</td>
            <td>Low level</td>
            <td><p>Captures UK implementation of NCTS5</p> <p>Shows NCTS5 process flows</p> <p>Lists the message definitions and rules and conditions involved in the exchange of messages between traders and the NCTS for the departure and arrival of transit movements</p></td>
            <td><p>Software developers</p> <p>Technical architects </p> <p>Product managers</p> <p>Business analysts</p></td>
        </tr>
        <tr>
          <td><a href="https://developer.service.hmrc.gov.uk/guides/ctc-traders-phase5-service-guide/">CTC Traders API phase 5 service guide</a></td>
            <td>Technical</td>
            <td>High level</td>
            <td><p>How to use the API</p> <p>How to self-onboard</p></td>
            <td><p>Software developers</p> <p>Technical architects</p></td>
        </tr>
        <tr>
            <td><a href="https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/2.1/oas/page">CTC Traders API v2.1 reference</a></td>
            <td>Technical</td>
            <td>Low level</td>
            <td>How to use each API endpoint</td>
            <td><p>Software developers</p> <p>Technical architects</p></td>
        </tr>
        <tr>
            <td>CTC Traders API phase 5 testing guide (this document)</td>
            <td>Functional</td>
            <td>Low level</td>
            <td><p>How to carry out assurance testing of your application software to ensure that it is compatible with the API</p> <p>How to carry out production access testing of your software</p></td>
            <td><p>Software developers</p> <p>Technical architects </p> <p>Product managers</p> <p>Business analysts</p></td>
        </tr>
    </tbody>
</table>


The order in you which you might read these documents can depend on whether you have previous NCTS experience. The following table recommends 2 possible reading orders but you can read the documents in any order you want.

| Suggested reading order | New NCTS users                    | NCTS4 users migrating to NCTS5    |
|-------------------------|-----------------------------------|-----------------------------------|
| 1                       | Roadmap                           | Service guide                     |
| 2                       | Service guide                     | Technical interface specification |
| 3                       | Technical interface specification | Reference                         |
| 4                       | Reference                         | Testing guide                     |
| 5                       | Testing guide                     | Roadmap                           |

**Note:** If you have NCTS4 experience,  it is important that you read the NCTS5 service guide and API reference carefully to understand all of the differences between NCTS4 and NCTS5. Reading only the NCTS5 technical interface specification will NOT guide you about all of the differences between the 2 NCTS phases.

## Related documentation

- [CTC Traders API v2.0 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.0-changelog) (GitHub)
- [CTC Traders API v2.1 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.1-changelog) (GitHub)
- [CTC Guarantee Balance API phase 5 testing guide](/guides/ctc-guarantee-balance-phase5-testing-guide/)
- [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R5_111023_v1.0.xlsx)
- [Transit Manual Supplement](https://www.gov.uk/government/publications/transit-manual-supplement) - UK transit procedures (OpenDocument Text document)

## Getting help and support

Before contacting us, find out if there is planned API downtime or a technical issue by checking [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk) and [New Computerised Transit System service availability](https://www.gov.uk/guidance/new-computerised-transit-system-service-availability).

If you have specific questions about the CTC Traders API, contact our Software Developer Support (SDS) Team. You’ll get an initial response within 2 working days.

You can also email questions to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk). We might ask for more detailed information when we respond.

## Changelog

You can find the changelog for this document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.
