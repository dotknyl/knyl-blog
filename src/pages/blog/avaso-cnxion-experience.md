---
title: "My Work Experience at Avaso / CNXION"
description: "A summary of my backend, frontend, and platform work across Avaso and CNXION."
pubDate: "2026-04-15"
heroImage: "/profile.jpg"
---

## Overview

I am a full-stack software engineer with around 2 years of experience working on Avaso / CNXION products. My work covers both backend and frontend, with a strong focus on building practical features, improving platform design, and solving workflow issues across internal systems.

Most of my work has been in .NET and Angular, with hands-on involvement in APIs, UI flows, background jobs, integrations, data models, and infrastructure-related troubleshooting.

## Main Areas of Work

### Backend Development

- Built and maintained services and APIs in .NET / ASP.NET Core.
- Worked with PostgreSQL, MongoDB, Hangfire, Azure App Configuration, and Key Vault.
- Implemented business logic for customs and trade workflows in the Avaso Bolt platform.
- Improved event-driven flows, background job processing, and integration reliability.

### Frontend Development

- Built and updated Angular UI features for internal business systems.
- Worked on forms, data capture flows, file upload handling, supporting documents, and validation-related UI.
- Helped connect frontend behavior with backend APIs and domain workflows.
- Participated in Angular upgrade and monorepo migration work.

### Platform and Domain Work

- Worked deeply with Customs-related modules, including Customs Orders, Declarations, CBAM, and EUDR features.
- Contributed to the Gist architecture for data federation, reporting, and dashboard visibility.
- Helped improve SLA tracking and milestone visibility by designing and implementing milestone-focused gist records.
- Designed and implemented feature access token flows for Customs Portal and EUDR-related access scenarios.

## Selected Contributions

### SLA Performance and Milestone Gists

One important area I worked on was improving SLA visibility.

The default SLA gist only showed header-level data, which was not enough for dashboards or for understanding milestone-level performance. To solve this, I created additional gist support focused on milestone records. This included updates to the record model, related logic, and frontend support so the data could be used more effectively in dashboards.

### FTP Inbound Alert System

I implemented an FTP inbound alert system so connector failures would not be missed.

This included backend logic for sending alert emails, configuration for recipient lists, and admin support for managing where alerts should be sent.

### Feature Access Tokens for Customs Portal

I worked on feature access token support for Customs Portal authorization.

This included using scoped tokens with `EntityType` and `EntityId`, and aligning the design so the Customs Portal communicates through the Customs API instead of calling the Config API directly. This work supports flows such as EUDR reminders and entity-specific access validation.

### EUDR and Trade Data Improvements

I worked on EUDR-related data handling, questionnaire logic, and supporting models.

I also investigated data consistency issues, including cases where duplicate commodity rows caused incorrect questionnaire completion checks. I proposed and implemented logic to use the latest commodity data record instead of picking the wrong row.

### Validation and Annotation Improvements

I contributed to a more flexible validation and annotation approach for transactional data.

This included working with field-level annotations, validation traces, and better ways to surface rule failures and normalization information for users.

## Technical Stack

- **Backend:** C#, .NET, ASP.NET Core
- **Frontend:** Angular, TypeScript, JavaScript
- **Database:** PostgreSQL, MongoDB
- **Infrastructure / Platform:** Hangfire, Azure App Configuration, Azure Key Vault, GitHub Packages
- **Other Areas:** Event-driven processing, integrations, reporting, validation engines, data federation

## Working Style

I usually work across both backend and frontend in the same feature area. I enjoy solving domain-heavy problems, improving system design, and turning unclear business needs into practical technical solutions.

A big part of my work is not only building new features, but also investigating edge cases, fixing root causes, and improving maintainability for future development.

## Summary

My experience at Avaso / CNXION has been a mix of product development, platform improvements, and technical problem-solving.

I have worked across customs workflows, internal tools, portal access, data federation, UI improvements, and backend services, with a focus on building solutions that are practical, reliable, and easier for teams to use and maintain.
