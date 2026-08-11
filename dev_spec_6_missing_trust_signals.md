# Missing trust signals — dev spec
Site: allbirds.com · Priority 6 · High · Effort: Medium (2-5 days)

## Problem
The homepage lacks visible trust elements like review counts, guarantees, or shipping policy details, which are critical for first-time visitors to overcome skepticism about comfort and quality.

## Evidence (from the live site)
> Body sample shows 'Free ground shipping on orders over $100' but no review counts, guarantee badges, or explicit return policy visible in the hero; trust flags indicate reviews and guarantee exist but are not prominent.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: The hero only has the headline and a generic CTA; no social proof or risk-reversal elements are visible.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Add a trust bar below the hero with '30-Day Guarantee', 'Free Shipping & Returns', and a star rating with review count (e.g., '4.8/5 from 20,000+ reviews') to neutralize objections about comfort and fit.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a trust bar below the hero with '30-Day Guarantee', 'Free Shipping & Returns', and a star rating with review count (e.g., '4.8/5 from 20,000+ reviews') to neutralize objections about comfort and fit.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_trust_signals` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
