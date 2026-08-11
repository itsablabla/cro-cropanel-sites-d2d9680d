# Shipping delay warning buried — dev spec
Site: allbirds.com · Priority 10 · High · Effort: Medium (2-5 days)

## Problem
The warning about up to 30-day shipping delays is only in the body text, not near the price or add-to-cart, creating an expectation gap that may lead to refunds and dissatisfaction.

## Evidence (from the live site)
> Body sample: 'Due to increased demand, orders may take up to 30 days to ship.' appears in the body text but not near product prices or CTAs.

## Current state
h1: Anytime Ankle Sock; cta: Learn More; notes: Shipping delay warning not visible near price or add-to-cart.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Display a prominent notice near the price: 'Orders may take up to 30 days to ship' to manage expectations.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display a prominent notice near the price: 'Orders may take up to 30 days to ship' to manage expectations.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_warning_buried` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
