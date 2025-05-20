# Project Proposal: VERVE
## Problem Statement

In today’s digital age, people are overwhelmed with news from countless sources, often struggling to find credible and relevant information. Our platform emphasizes **credibility and inclusivity** by featuring verified reports from official publishers, while keeping uncertified content separate to prevent misinformation and protect free speech.

Additionally, many find traditional newsstands or newspapers inconvenient. VERVE removes these barriers by delivering curated news directly to users’ devices, offering a modern, engaging, and easy-to-access experience.

## Objectives

* Develop a web-based application that aggregates news from multiple reliable sources.
* Implement user-specific customization for personalized news feeds.
* Provide real-time updates to keep users informed of the latest developments.
* Ensure a user-friendly, intuitive interface to enhance the news reading experience.
* Facilitate quick and easy access to breaking news.

## Target Users

* Individuals seeking a personalized and efficient way to consume news.
* Users who want a curated and aesthetically pleasing news feed tailored to their preferences.

## Technologies and Frameworks

### Backend

* Java 17 with Spring Boot for robust, scalable RESTful APIs.
* Integration with external weather APIs.
* PostgreSQL for efficient database management.

### Frontend

* HTML, CSS, and Vanilla JavaScript.
* HTTP session management for user sessions.

### Additional Tools

* Git for version control and collaboration.

## Expected Design Patterns

* **Model-View-Controller (MVC):** To separate concerns between data, UI, and business logic for maintainable code.
* **Observer Pattern:** For real-time notifications about new articles or updates.
* **Singleton Pattern:** To manage single instances of core services like news fetching.

## High-Level System Overview

### News App Structure

1. **User Authentication**

   * Login with username & password.

2. **Onboarding & Personalization**

   * Users select at least one news category to receive tailored recommendations.

3. **Main Interface**

   * **Newspaper (Home Page):** Personalized feed based on followed categories.
   * **Surprise Me:** Trending news beyond user preferences.
   * **Community Discussions:** Reddit-style threads with upvotes & comments.

4. **Social Features**

   * Follow other users to see their posts and comments.
   * Pin articles instead of liking.

5. **Publishing**

   * Floating pen icon to create news posts.
   * Posts require title, content, and optional media.

6. **Post / Newsletter View**

   * Expandable articles with comments and live debates.
   * Real-time fact-checking flags misinformation.

7. **New Features**

   * Real-time alerts, story rewrites, multi-language support, reading modes (time-based, brief, distraction-free).

8. **Certification**

   * Verified publishers submit ID/business docs and social media reviews.

9. **Publishing System**

   * Verified publishers and trusted users can publish.
   * Posts categorized with hashtags, media attachments, and grammar checks.

## Requirements Specification

### Functional Requirements

* Account creation, login, logout, password recovery.
* Personalized news feed and publisher following.
* Article creation, publishing, and basic grammar check.
* Engagement: pinning, commenting, sharing, discussions, debates.
* Fact-checking and content moderation.
* Real-time alerts and daily digests.
* Publisher verification.
* Multi-language AI-powered translations.
* Distraction-free and brief reading modes.

### Non-Functional Requirements

* Scalability to support many concurrent users.
* High availability and uptime.
* Intuitive, mobile-responsive UI.
* Modular architecture for easy maintenance and extension.

### System Constraints

* Dependence on external Weather APIs.
* High computational load for real-time updates.
* Latency and accuracy challenges with AI translations.
* Scalability challenges in content moderation.

### Assumptions & Dependencies

* Moderate initial user base with scalability plans.
* Active user engagement in discussions and moderation.
* Compliance with data privacy and content policies.
* Stable internet connections.
* Primary access through desktop and mobile browsers.

## System Architecture Design

### Selected Design Patterns & Justification

* **Observer:** For notification handling via publisher-subscriber relationships.
* **Strategy:** Dynamic article filtering algorithms without code modification.
* **DTO (Data Transfer Object):** Separates data communication from domain models.
* **MVC:** Clear separation of data, UI, and business logic.
* **Singleton:** Single instances of core services managed by Spring.
* **Factory Method:** Object creation and configuration separation using Spring @Bean methods.

## Class Responsibilities Overview

| Class Name      | Role                                | Responsibilities                                              |
| --------------- | ----------------------------------- | ------------------------------------------------------------- |
| NewsAggregator  | Central coordinator                 | Manages news aggregation workflow and coordinates components. |
| NewsSource      | External news source representation | Fetches articles from specific sources with modular logic.    |
| NewsArticle     | Data model for articles             | Stores article data and formatting methods.                   |
| NewsCategory    | Categorizes news                    | Groups articles by topic for filtering and display.           |
| UserPreferences | User-specific settings              | Stores and applies user filters for tailored content.         |
| NewsDisplay     | UI presentation                     | Formats and displays filtered news articles.                  |
| NewsFetcher     | Data retrieval abstraction          | Handles fetching articles from multiple sources.              |

## Class Relationships Summary

* **NewsAggregator** interacts with multiple **NewsSource** instances.
* **NewsCategory** groups related **NewsArticle** objects.
* **UserPreferences** selects relevant **NewsCategory** and filters **NewsArticle**.
* **NewsDisplay** renders filtered articles based on **UserPreferences**.
