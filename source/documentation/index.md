---
title: CTC Traders phase 5 testing guide
weight: 1
description: Software developers, designers, product owners or business analysts. Verify the compatibility of your software with CTC Traders API and learn how to test your application in our sandbox environment.
---

# CTC Traders API phase 5 testing guide

Verify the compatibility of your software with [CTC Traders API v2.0](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/common-transit-convention-traders/2.0) and learn how to test your application in our sandbox environment.

## Before you start

When you are ready to test your software, first read and understand the [CTC Traders API phase 5 service guide](/guides/ctc-traders-phase5-service-guide/).

We strongly advise you to start testing your software for compatibility purposes as soon as possible.

### Test environments

#### Trader Test

Trader Test simulates automated responses. It also provides an environment in which New Computerised Transit System (NCTS) support staff simulate the tasks done by Border Force personnel.

Trader Test enables you to check that your software is fully compatible with the CTC Traders API. Using Trader Test to validate the compatibility of your software is a prerequisite to being given access to the live production environment.

#### CTC Traders Test Support API

The CTC Traders Test Support API enables you to inject transit movement notifications as if they have been sent by the NCTS from a customs office of departure or destination. Until automated responses to trader messages are supported in a Trader Test environment, the API enables responses to be triggered manually. 

**Note:** The CTC Traders Test Support API is not a substitute for Trader Test. It will be switched off as soon as Trader Test becomes available.

You must make requests to the CTC Traders Test Support API in JSON format. The API injects messages in XML format.

For more information, see [CTC Traders Test Support API specification](/api-documentation/docs/api/service/common-transit-convention-traders-test-support/2.0).

### Testing process

....?

### Testing prerequisites

Before you start testing, you should:

1. complete the getting started steps in [CTC Traders API phase 5 service guide](https://developer.service.hmrc.gov.uk/guides/ctc-traders-phase5-service-guide/)
2. ??

## Related documentation

- [CTC Traders API roadmap](/roadmaps/common-transit-convention-traders-roadmap/)
- [CTC Traders API v2.0 reference](/api-documentation/docs/api/service/common-transit-convention-traders/2.0/oas/page)
- [CTC Traders API v2.0 changelog](https://github.com/hmrc/common-transit-convention-traders/wiki/CTC-Traders-API-v2.0-changelog) (GitHub)
- [NCTS phase 5 technical interface specification](/guides/ctc-traders-phase5-tis/)
- [NCTS phase 4-phase 5 data mapping spreadsheet](https://github.com/hmrc/ctc-traders-phase5-tis/blob/main/source/figures/NCTS-P5_Datamapping_R2_190123_v1.0.xlsx) (GitHub)

## Getting help and support

Before contacting us, find out if there is planned API downtime or a technical issue by checking [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk/?_ga=2.139406967.536493967.1674469117-2060941422.1667396839) and [New Computerised Transit System service availability](https://www.gov.uk/guidance/new-computerised-transit-system-service-availability?_ga=2.174532070.536493967.1674469117-2060941422.1667396839).

If you have specific questions about the CTC Traders API, contact our Software Developer Support (SDS) Team. You’ll get an initial response within 2 working days.

You can also email questions to [SDSTeam@hmrc.gov.uk](mailto:SDSTeam@hmrc.gov.uk). We might ask for more detailed information when we respond.

## Changelog

You can find the changelog for this document in the [ctc-traders-phase5-testing-guide](https://github.com/hmrc/ctc-traders-phase5-testing-guide/wiki/CTC-Traders-API-phase-5-testing-guide-changelog) GitHub wiki.
