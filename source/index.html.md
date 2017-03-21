---
title: API Reference

language_tabs:
  - javascript--airwatch: AirWatch
  - javascript--mobileiron: MobileIron

toc_footers:
  - <a href='https://github.com/AppDirect/mdm-service'>MDM Service</a>

includes:
  - create-company
  - setup-company
  - user-membership-added
  - user-membership-removed
  - application-subscription-added
  - application-subscription-removed
  - application-assignment-added
  - application-assignment-removed
  - authorize-device
  - unauthorize-device

search: true
---

# Introduction

This API documentation is intented for MDM providers to integrate with AppDirect's MDM Microservice.

With this documentation, MDM providers will see the general workflow from AppDirect's Marketplace and will have an idea on what API's are needed to make the integration work.

This documentation is written to be generic. It is possible to have multiple API calls for a single AppDirect workflow.

The MDM Microservice is built in such a way that it can cater to different implementations of the MDM providers and store different provider models accordingly.
