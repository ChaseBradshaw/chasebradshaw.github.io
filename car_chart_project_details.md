DOC_ID: CAR_CHART.TXT
Status: Active Development / Private Alpha
Car Chart

AI-powered auction analytics & canonical vehicle data platform
A full-stack data platform designed to automate vehicle research, normalize auction data, and surface market insights for car buyers. Car Chart combines AI-driven research, human-in-the-loop validation, and large-scale auction scraping to build a canonical vehicle database that traditional analytics tools struggle to maintain.

Why This Exists

Car auction data is messy. Listings vary wildly in naming, trim details, and structure — making meaningful analytics nearly impossible without a clean, canonical dataset.

Building that dataset manually (Make → Model → Generation → Trim) is slow, error-prone, and doesn’t scale.

The challenge:
How do you build a reliable, evolving vehicle hierarchy while ingesting thousands of inconsistent auction listings?

Architecture Overview

Car Chart is designed as a modular, containerized system with clear separation between orchestration, background workers, and human review.

Core components:

AI Research Agent
Discovers vehicle models, generations, and trims using LLMs and structures the results into staging tables.

Human-in-the-Loop Review UI
A web dashboard for approving, editing, or rejecting AI-generated data before it enters the canonical dataset.

Queue-Based Scraper System
Worker containers claim jobs from a database-backed queue and scrape auction data asynchronously.

Canonical Database Layer
A normalized PostgreSQL schema that enforces consistency across makes, models, generations, trims, and auctions.

The API and worker services share a database and log volume — eliminating unnecessary network coupling while maintaining observability.

Key Technical Decisions
Human-in-the-Loop by Design

AI accelerates discovery, but correctness matters.
All AI-generated vehicle data enters staging tables and must be explicitly reviewed before promotion to canonical records.

This prevents data drift while still allowing rapid expansion.

Matching & Deduplication Logic

To avoid duplicates and fragmentation, the system performs automated matching using:

Internal generation codes (e.g. E46, F80)

Normalized string comparisons

Fuzzy matching thresholds for trims and aliases

Suggested matches are presented during review — speeding approval without sacrificing accuracy.

Scalable Scraping Architecture

Queue-based job execution using database locks (FOR UPDATE SKIP LOCKED)

Isolated worker containers with supervised scraper processes

Per-auction error handling to ensure long-running jobs continue safely

Optional extraction of bids, comments, and metadata

This allows scraping to scale independently from the UI and API layer.

Tech Stack (EXECUTABLES)

You can present these as tags like your other project:

Python / FastAPI

PostgreSQL (Supabase)

Docker & Docker Compose

Selenium

LLMs (Research Agent)

REST APIs

Queue-based workers

Custom admin UI

Role & Ownership
Contribution

 System architecture & data modeling

 AI research orchestration

 Queue-based worker design

 Scraper engine & extractors

 Admin & review UI

 Matching & validation logic

This is where you clearly establish: solo architect, solo builder.