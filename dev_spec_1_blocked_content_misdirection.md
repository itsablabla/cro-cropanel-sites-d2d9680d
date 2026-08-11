# Blocked content misdirection — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Low (0.5-2 days)

## Problem
The hero contains multiple H1s that are 'blocked' messages, indicating a rendering issue that prevents visitors from seeing the intended message, causing confusion and distrust.

## Evidence (from the live site)
> H1s include: 'shop.app is blocked', 'www.allbirds.com is blocked' (repeated 4 times)
> H1s include 'shop.app is blocked' and 'www.allbirds.com is blocked' repeated five times; body sample shows 'shop.app is blocked' and 'www.allbirds.com is blocked'.
> H1s include 'shop.app is blocked' and multiple 'www.allbirds.com is blocked'; title is 'shop.app' instead of Allbirds; no meta description or canonical.
> SEO title: 'shop.app', H1s: 'shop.app is blocked', 'www.allbirds.com is blocked' (repeated 4 times).

## Current state
h1: Wildly Comfortable. Super Natural. (plus 5 blocked messages); cta: Shop All; notes: The presence of 'blocked' messages in the H1s suggests that the hero section is not loading correctly for some visitors, potentially due to ad blockers or script errors, which undermines the credibility of the page.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Ensure the hero content is server-side rendered or uses fallback text that is not blocked by ad blockers. The hero should always display the intended message without any 'blocked' placeholders.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure the hero content is server-side rendered or uses fallback text that is not blocked by ad blockers. The hero should always display the intended message without any 'blocked' placeholders.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_blocked_content_misdirection` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
