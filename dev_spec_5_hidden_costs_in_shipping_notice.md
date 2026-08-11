# Hidden costs in shipping notice — dev spec
Site: allbirds.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
The free shipping threshold is not clearly communicated upfront; the notice 'Free ground shipping on orders over $100' is buried in the body text, and the 'Due to increased demand, orders may take up to 30 days to ship' warning may deter immediate purchase due to perceived delay.

## Evidence (from the live site)
> Body sample: 'Free ground shipping on orders over $100 Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Shipping threshold and delay warning are in small text, not prominent; users may not see them until checkout.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Place free shipping threshold and delivery estimate near CTAs or in a banner; consider offering free shipping with no minimum to reduce friction.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Place free shipping threshold and delivery estimate near CTAs or in a banner; consider offering free shipping with no minimum to reduce friction.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_hidden_costs_in_shipping_notice` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
