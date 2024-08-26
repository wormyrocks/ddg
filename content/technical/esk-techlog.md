---
title: evan tech log
draft: false
tags:
  - meta
---
# To do

- [ ] add links to writing from cohost
- [ ] pdf preview show up at correct size
- [ ] static dataview plugin to sort stuff by dates
- [ ] slideshow view

obsidian - advanced slides

## changes 8/25/2024

* started using #meta tag for pages that are about the site / building it
- experimented a bit with folder pages
	- example =>[[technical/]]
	- added more info on how they work[[how-to#subpages / folder pages|here]]
	- converted `writings and notes index.md` into folder page for [[writings/]]
		- ok, but that means we lose the dates for each document. so we need to add dates to the frontmatter of each subpage to get them to sort properly
		- => quartz will override the 'last modified' field on a page if you use the `date` tag in frontmatter (looks like previously we were calling it `from`)
		- that means the auto-generated folder listing on our [[writings/]] page sorts by actual date written!
		- in case we want to leverage this elsewhere, also noticed that the `from` property was also being used on [[07-21-2018|this page]] - renamed it to `date`
			- side benefit of this change: we now have an automatically sorted [[memories/by year/2018|2018 memories]] folder page!
