---
title: notes on how to update the site
draft: false
tags:
---
# key sources
* [obsidian / markdown cheat sheet](https://publish-01.obsidian.md/access/09cfa50ec31c0f01873549787f02a7e0/assets/Markdown%20Cheat%20Sheet.pdf)
* [quartz documentation](https://quartz.jzhao.xyz/authoring-content)
* [nicole vanderhoeven youtube video](https://www.youtube.com/watch?v=6s6DT1yN4dw)
	* [associated notebook](https://notes.nicolevanderhoeven.com/How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages)
* [morrowind modding wiki](https://morrowind-modding.github.io/contributing/how-to-contribute) (good instructions for beginners wishing to contribute to quartz vault)
# steps
please feel free to add more detail to these as needed

everyone probably needs to do this:
* install [obsidian](https://obsidian.md/)
* install [github](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop) and clone [this repository](https://github.com/wormyrocks/ddg)

git-friendly workflow:
1. install [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm#using-a-node-installer-to-install-nodejs-and-npm)
2. clone repository: `git clone https://github.com/wormyrocks/ddg`
3. install dependencies: `cd ddg; npm i`
4. `npx quartz build --serve` to preview, opens at http://localhost:8080
5. install obsidian, open the directory `ddg` as vault to edit and preview locally
6. `npx quartz sync` to push to git

non-git workflow:
use [noteshub](https://about.noteshub.app/)?
use [pull](https://github.com/apps/pull)?

# todo
domain
themes?
general organization / hierarchy

# random notes

base url is stored in `quartz.config.ts`  
`ctrl+o` searches for a file  
`ctrl+p` searches for a command  
`ctrl+e` switches between edit and view modes  
`ctrl+,` opens preferences  

**in markdown, the most annoying thing to remember is that you need to use two spaces before it will insert a new line lol**

## adding a new page

creating a new page requires adding frontmatter. the file should be created in `content/` and should be created from `template/default.md`. so in obsidian this looks like:
* `Ctrl-P` -> `Create New Note`
	* make sure the file shows up in the `content/` folder, this should be on by default but might not stick. i am overriding gitignore to add `.obisidan/app.json`, and `.obsidian/templates.json` hopefully this does not cause problems in the future
* `Ctrl-P` -> `Templates: Insert template` -> `default`
* then you should have a new page that lets you enter a title, tags, and mark it as a draft.
	* not quite sure how marking something as a draft behaves. will investigate with [[draft test]].

## embeds

you should be able to drag and drop pictures into obsidian and if all goes right it should get copied into `/media`.

for youtube stuff, it looks like you can embed with this syntax:

```
![](https://www.youtube.com/watch?v=7YdgvjE7dA0)
```

(see [[test#a video]])
