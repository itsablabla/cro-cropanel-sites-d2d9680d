# Spec-forward hero copy — dev spec
Site: allbirds.com · Priority 4 · High · Effort: Low (0.5-2 days)

## Problem
The hero headline 'Wildly Comfortable. Super Natural.' is abstract and feature-led, failing to directly address the visitor's intent to find comfortable, sustainable shoes, and the CTA 'Shop All' is generic, lacking urgency or clarity.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.'
> CTA: 'Shop All'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: The headline is vague and doesn't mention shoes or the visitor's need for comfort and sustainability. The CTA is generic and doesn't guide the visitor to a specific next step.

## Required change
h1: Shoes That Feel Like Nothing. Made from Nature.; cta: Shop Best Sellers; notes: The headline directly addresses the visitor's likely intent (comfort and sustainability) and the CTA is more specific, leading to a curated collection that helps the visitor find what they need faster.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN The headline directly addresses the visitor's likely intent (comfort and sustainability) and the CTA is more specific, leading to a curated collection that helps the visitor find what they need faster.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_spec_forward_hero_copy` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
