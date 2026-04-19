# Task 01 — SERP Feature Extraction & Structured Scoring

## Setup

npm install

## Run Tests

npx jest

## Run Against All 30 SERP Examples

npx ts-node src/runAll.ts

## How It Works

The scoreSERP function reads a SERP input, finds which features
are true, adds up their weights, and returns a score capped at 100.

Higher score = harder to get organic clicks from Google.

## Example

Input:

- keyword: "best running shoes"
- featured_snippet: true (25 pts)
- people_also_ask: true (10 pts)
- shopping_ads: true (20 pts)

Output:

- competition_score: 55
- detected_features: ["featured_snippet", "people_also_ask", "shopping_ads"]

## Dependencies Used

- typescript — write type-safe code
- ts-node — run TypeScript directly without compiling
- jest — run unit tests
- ts-jest — makes Jest understand TypeScript files
- @types/jest — TypeScript definitions for jest functions

## How to Support Custom Weights Per Client

Pass an optional customWeights object into the function.
If a client provides their own weights, use those instead of
the defaults. This way each client can decide how much each
feature matters for their business.

Example:
scoreSERP(input, { local_pack: 50, shopping_ads: 10 })
