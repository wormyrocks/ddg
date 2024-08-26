---
title: evan tech log
draft: false
tags:
  - meta
---
# To do

- [x] add links to writing from cohost
- [x] pdf preview show up at correct size
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
- fixing pdf height
	- [stack overflow to the rescue](https://stackoverflow.com/questions/72381658/how-to-embed-pdf-within-an-iframe-with-height-exactly-one-page) - it's a quartz bug!
	- changed default pdf embed style in `transformers/ofm.ts` to set `style= width:100%;` for all pdf embeds
	- getting fancy: ok, the quartz composer will now automatically set the aspect ratio if you put it in the metadata
		- sorta branching off this: https://help.obsidian.md/Linking+notes+and+files/Embed+files#Embed+a+PDF+in+a+note
		- updated the quartz pdf emitter so it will read the image dimension tags in the same way that the image emitter does
		- tadaaa! [[Builders]] (it won't show up properly in obsidian, but should work on the deployed site)
- static dataview plugin
	- to come back to: dataview example [here](https://quartz.eilleeenz.com/tbd/Dataview-reference)
	- probably oughtta use this plugin https://github.com/dsebastien/obsidian-dataview-serializer
- slides
	- NVDH has a [video on this](https://www.youtube.com/watch?v=LtBK_iNcVEQ)
		- it's [not being built into quartz directly](https://github.com/jackyzha0/quartz/issues/955)
		- probably just need to use reveal.js or splide directly and then add a slide compile into the build steps
- added cohost pages
	- [[the-tower]]
	- [[on-bottomless-pits]]
	- [[boundless-network-cyberspace]]
	- copied the header images from cohost posts
	- no good way to make images take up 100% of page size in obsidian, but if you just set width to something arbitrarily large (2000 worked?) they get auto-shrunk by quartz
- set `New Note` to open a new note in 'current folder' rather than in `content/`
- updated keyboard shortcuts (sorry, everyone else):
	- `Alt+H`, `Alt+J`, `Alt+K`, `Alt+L` for navigating between panes
	- `Ctrl+Alt+B` for toggling left sidebar
	- `Ctrl+Alt+H` for toggling right sidebar
	- `Ctrl+Alt+J` to split down
	- `Ctrl+Alt+L` to split right