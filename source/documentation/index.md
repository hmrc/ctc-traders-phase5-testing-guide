---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Verify the compatibility of your software with CTC Traders API and learn how to test your application in our sandbox environment.
---

# CTC Traders API phase 5 testing guide

Learn how to test the compatibility of your software with New Computerised Transit System phase 5 (NCTS5) and [CTC Traders API v2.0](/api-documentation/docs/api/service/common-transit-convention-traders/2.0).

[Learn about key NCTS5 dates](/guides/ctc-traders-phase5-tis/#ncts5-key-dates).

**Note:** Please restrict your testing to the test scenarios in this document. HMRC cannot support tests that are not included here.

## Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/) and [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/) if you have not already done so. It is also advisable to review the [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R5_111023_v1.0.xlsx) so that you understand differences in message types between NCTS4 and NCTS5.

### Testing cycles

As part of ensuring your readiness for go-live of the UK NCTS5 service, you will have to complete at least 2 testing cycles prior to this.

| Cycle | Description | Start date | End date | Scope | Message fields |
| ----- | ----------- | -------------- | ----- | ----- | ----- |
| Assurance | Before go-live, you will need to check that your software is compatible with both it and CTC Traders API v2.0. This involves using predefined test scenarios and test data. |  |  | Small messages (up to 5MB) | Mandatory and optional |
| | You have the option to send large messages to NCTS. Large message tests are based on the same test scenarios as small message tests. |  |  | Large messages (up to 8MB) | Mandatory and optional |
| Production access (2 phases) | **Phase 1: NCTS5 transition rules only**<br />This is your only opportunity to complete transition rules testing in NCTS5 Trader Test as part of your assurance and production access testing. <br /><br />You will not be able to receive production access for transition rules testing after summer 2024. This means that if you have not been granted production access for transition rules testing by summer 2024, you cannot use the NCTS5 service until the final rules are in place (see [NCTS5 key dates](/guides/ctc-traders-phase5-tis/#ncts5-key-dates)). | 30 October 2023 | Summer 2024 | Small messages <br /><br />Large messages (if applicable)<br /><br />Transition rules | Mandatory only |
|  | **Phase 2: NCTS5 final rules only**<br />During phase 2, you will complete your NCTS5 final rules testing in NCTS5 Trader Test as part of your assurance and production access testing. | Summer 2024 | (No end date) | Small messages <br /><br />Large messages (if applicable) | Mandatory only |

During summer 2024, the NCTS5 Trader Test environment will move back into NCTS5 final mode after the UK NCTS5 service goes live. We will tell you the exact date of the switchover nearer the time.

**Note:** The production credentials application form that you will use lists the test scenarios that must be run for production access testing. For more information about this form, see [Apply for production credentials](documentation/apply-for-production-credentials.html).

If you intend to use [CTC Guarantee Balance API v2.0](/api-documentation/docs/api/service/common-transit-convention-guarantee-balance/2.0):

- your NCTS5 assurance testing will also need to include testing the compatibility of your software with that API - for more information, see [CTC Guarantee Balance API phase 5 testing guide](/guides/ctc-guarantee-balance-phase5-testing-guide/)
- you do NOT have to apply for separate production credentials for that API - this is because production credentials for CTC Traders API v2.0 are sufficient for using the UK NCTS5 service after it goes live

### Test environments

You must use our sandbox environment and Trader Test to test the compatibility of your software with CTC Traders API v2.0.

#### Trader Test

Trader Test is a test environment that simulates both automated responses and real-life experience where NCTS support staff do the tasks of Border Force personnel. When your testing requires a manual response, NCTS support staff will perform the live manual steps of the process. This simulates and tests a full real-life journey from start to finish for you.

You can use NCTS5 Trader Test to test small messages (up to 5MB in size) and large messages (up to 8MB in size) with standard departures process flows, pre-lodged departures process flows, and arrivals process flows (as defined in this document).

**Note:** If you have an HMRC [developer account](/developer/login) and can access our sandbox environment, you have access to the NCTS5 Trader Test environment automatically.

### Testing prerequisites

For information about actions that must be completed before testing, see the getting started section of the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/#getting-started).

### Message sizes

CTC Traders API v2.0 supports both small (up to 5MB in size) and large (up to 8MB in size) messages. Both message sizes are testable in Trader Test.

### UK cutover from NCTS4 to NCTS5

After the UK NCTS5 service goes live, there will be a cutover period during which:

- the NCTS4 service will continue running only to deal with in-flight transit declarations submitted before the go-live date
- the NCTS5 service will handle all new transit declarations submitted from the go-live date onwards

### Transition period

The transition period is the period of time during which countries may switch to operating NCTS5 at any point and will run until all countries have switched to operating NCTS5. NCTS operations are currently considered to be in the transition period.

During the transition period, those countries that are operating NCTS5 must do so in transitional mode, which is equivalent to a 'backwards compatibility' mode. This is to ensure that messages can be exchanged between NCTS4 and NCTS5 countries, which is handled by an upgrade/downgrade convertor in the common domain, where messages are exchanged at country to country level. For example, notifying the country of destination that the movement has been released or notifying the country of departure that the movement has arrived, and so on.

To ensure backwards compatibility with NCTS4 during transition, special rules and conditions have been defined to restrict/prevent usage of new data fields and some functionality until all countries are operating NCTS5. This allows downgrading of NCTS5 messages to NCTS4.

The prefixes of these rules and conditions are as follows.

| Rule prefix | Description |
| ----------- | ----------- |
| B | Restrictive business rules effective during transitional period. |
| E | Restrictive technical rules effective during transitional period. |

During the transition period, NCTS will observe and apply these business ([Rules B](/guides/ctc-traders-phase5-tis/documentation/rules-b.html)) and technical ([Rules E](/guides/ctc-traders-phase5-tis/documentation/rules-e.html)) rules as defined in the [NCTS Phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/).

As part of your assurance and production access testing for NCTS5, you will need to run some predefined tests to verify how your software handles transition rules.

## Navigating CTC Traders API v2.0 documentation

The following table lists the documents for CTC Traders API v2.0 and outlines the content and intended readers of each document.

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
            <td><a href="https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/2.0/oas/page">CTC Traders API v2.0 reference</a></td>
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

| Suggested reading order | New NCTS users | NCTS4 users migrating to NCTS5 |
| --- | --- | --- |
| 1 | Roadmap | Service guide |
| 2 | Service guide | Technical interface specification |
| 3 | Technical interface specification | Reference |
| 4 | Reference | Testing guide |
| 5 | Testing guide | Roadmap |

**Note:** If you have NCTS4 experience,  it is important that you read the NCTS5 service guide and API reference carefully to understand all of the differences between NCTS4 and NCTS5. Reading only the NCTS5 technical interface specification will NOT guide you about all of the differences between the 2 NCTS phases.

## Related documentation

- [CTC Traders API v2.0 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.0-changelog) (GitHub)
- [CTC Guarantee Balance API phase 5 testing guide](/guides/ctc-guarantee-balance-phase5-testing-guide/)
- [NCTS phase 4-phase 5 data mapping spreadsheet](/guides/ctc-traders-phase5-tis/downloads/NCTS-P5_Datamapping_R5_111023_v1.0.xlsx)
- [Transit Manual Supplement](https://www.gov.uk/government/publications/transit-manual-supplement) - UK transit procedures (OpenDocument Text document)

## Getting help and support

Before contacting us, find out if there is planned API downtime or a technical issue by checking [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk) and [New Computerised Transit System service availability](https://www.gov.uk/guidance/new-computerised-transit-system-service-availability).

If you have specific questions about the CTC Traders API, contact our Software Developer Support (SDS) Team. You’ll get an initial response within 2 working days.

You can also email questions to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk). We might ask for more detailed information when we respond.

## Changelog

You can find the changelog for this document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.
