# Misleading blocked page title — dev spec
Site: allbirds.com · Priority 2 · Urgent · Effort: Medium (2-5 days)

## Problem
The homepage title is 'shop.app' and the H1s include 'www.allbirds.com is blocked', which misrepresents the site and can confuse users, damaging trust and potentially causing them to leave.

## Evidence (from the live site)
> SEO title: 'shop.app', H1s: 'shop.app is blocked', 'www.allbirds.com is blocked' (repeated 4 times).

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Title tag is 'shop.app' and H1s include 'www.allbirds.com is blocked'.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Fix title tag to 'Allbirds | Comfortable Sustainable Shoes & Apparel' and remove any 'blocked' H1s.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Fix title tag to 'Allbirds | Comfortable Sustainable Shoes & Apparel' and remove any 'blocked' H1s.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_misleading_blocked_page_title` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
