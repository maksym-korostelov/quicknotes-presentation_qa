# QuickNotes Workshop — Cross-Platform Mapping Guide

This document is a reference for the GitHub Copilot Workshop Assistant. It contains cross-platform mapping tables and platform-specific examples for all streams (iOS, Android, BE, FE, QA, Automation QA).

---

## Architecture Mapping

| iOS (Demo) | Android (Demo) | Backend | Frontend |
|------------|----------------|---------|----------|
| SwiftUI View | Jetpack Compose Screen | REST Controller / GraphQL Resolver | React/Vue/Angular Component |
| ViewModel (`@Observable`) | ViewModel (`StateFlow`) | Service Layer | Hooks / Store / Service |
| UseCase | UseCase | Service / UseCase | Custom Hook / Service |
| Entity (struct) | Entity (data class) | Entity / Model / DTO | Interface / Type / Model |
| Repository Protocol | Repository Interface | Repository Interface | API Service Interface |
| Repository Impl | Repository Impl | Repository Impl | API Service Impl |
| SwiftData Model | Room Entity | JPA Entity / ORM | N/A |
| InMemory Repository | Local DataSource | JPA Repository / ORM | LocalStorage / IndexedDB |
| AppTypography (ViewModifier) | AppTypography (TextStyle object) | N/A | Design tokens / CSS variables |
| AppColors (semantic) | AppColors (semantic) | N/A | Theme colors / CSS custom properties |

---

## Instruction Files — Platform Examples

| Platform | Example Instructions Content |
|----------|------------------------------|
| **iOS** | SwiftUI patterns, Swift naming conventions, iOS architecture rules |
| **Android** | Kotlin coding standards, Compose guidelines, Android architecture |
| **BE** | API design patterns, error handling, logging standards, REST conventions |
| **FE** | Component structure, state management patterns, TypeScript conventions |
| **QA** | Test case format, bug report template, testing checklists |
| **Automation QA** | Test naming conventions, page object patterns, assertion styles |

---

## Prompt Files — Platform Examples

| Platform | Useful Prompt Templates |
|----------|-------------------------|
| **iOS** | SwiftUI View, ViewModel, UseCase, XCTest unit test, typography migration |
| **Android** | Composable, ViewModel, UseCase, JUnit test, iOS-to-Android migration |
| **BE** | REST Controller, Service, Repository, Integration test |
| **FE** | React Component, Custom Hook, API Service, Jest test |
| **QA** | Test case from requirements, bug report, test plan |
| **Automation QA** | Page Object, Test fixture, E2E test scenario |

---

## MCP — Platform Use Cases

| Platform | MCP Use Cases |
|----------|---------------|
| **iOS** | Connect to design system, fetch API specs, access CI/CD |
| **Android** | Same as iOS + Firebase integration |
| **BE** | Database schema access, API documentation, monitoring tools |
| **FE** | Design tokens, CMS content, feature flags |
| **QA** | Test management systems (Jira, TestRail), requirements docs |
| **Automation QA** | Test data generators, environment configs, reporting tools |

---

## Code Review — Platform Focus Areas

| Platform | Review Focus |
|----------|-------------|
| **iOS** | Memory management, SwiftUI best practices, architecture compliance |
| **Android** | Lifecycle awareness, Compose performance, architecture compliance |
| **BE** | Security, performance, error handling, API design |
| **FE** | Accessibility, performance, component patterns, type safety |
| **QA** | Test coverage, edge cases, requirement traceability |
| **Automation QA** | Test stability, maintainability, proper assertions |

---

## Cross-Platform Guidance Template

Use this structure when providing cross-platform guidance in session content:

### For Android Developers
[How to apply this in Android/Kotlin context]

### For Backend Developers
[How to apply this in BE context with examples]

### For Frontend Developers
[How to apply this in FE context with examples]

### For QA Engineers
[How to apply this for manual testing workflows]

### For Automation QA Engineers
[How to apply this for test automation]
