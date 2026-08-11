# Mega-menu choice overload — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The mega-menu presents 20+ nav items with multiple subcategories and product links, overwhelming users and increasing cognitive load, which can lead to choice paralysis and reduced click-through.

## Evidence (from the live site)
> Nav items list includes 20 entries: 'New Arrivals', 'Shop All', 'Bestsellers', 'LEATHER ALTERNATIVES', 'Men's Shoes', 'Sneakers', 'Slip Ons', 'Sandals', 'Active', 'All-Weather', 'Runner NZ', 'Cruiser', 'Tree Runner NZ', 'Socks', 'Men's Apparel', 'Women's Shoes', 'Trainers', 'Flats', 'Canvas Cruiser', 'Women's Apparel'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Mega-menu with 20+ items, multiple subcategories, and product links.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Simplify mega-menu to top 5-7 categories, use clear hierarchy, and reduce subcategory links to avoid choice overload.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Simplify mega-menu to top 5-7 categories, use clear hierarchy, and reduce subcategory links to avoid choice overload.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_mega_menu_choice_overload` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
