# Multiple competing CTAs — dev spec
Site: allbirds.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The hero section presents multiple competing CTAs without a single clear primary action, diluting user focus and reducing click-through to a specific product category.

## Evidence (from the live site)
> CTAs listed: 'Shop All', 'Shop Womens', 'Shop Mens', 'Shop Socks', 'Shop Women's Sale', 'Shop Men's Sale' in the hero area
> H1: 'Wildly Comfortable. Super Natural.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Multiple: Shop All, Shop Womens, Shop Mens, Shop Socks, Shop Women's Sale, Shop Men's Sale; notes: Hero has no single primary CTA; users are presented with six options, causing decision paralysis.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Single primary CTA: 'Shop Bestsellers' or 'Shop Women's' (depending on target audience); notes: Reduce to one primary CTA and secondary links in nav; prioritize based on business goals.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Reduce to one primary CTA and secondary links in nav; prioritize based on business goals.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_competing_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
