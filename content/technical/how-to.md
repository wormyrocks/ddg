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

---

# steps
please feel free to add more detail to these as needed

everyone probably needs to do this:
* install [obsidian](https://obsidian.md/)
* install [github](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop) and clone [this repository](https://github.com/wormyrocks/ddg)
	* if you haven't used github before, [add your SSH credentials to your github account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

git-friendly workflow:
1. install [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm#using-a-node-installer-to-install-nodejs-and-npm)
2. clone repository: `git clone https://github.com/wormyrocks/ddg`
3. install dependencies: `cd ddg; npm i`
4. `npx quartz build --serve` to preview, opens at http://localhost:8080
5. install obsidian, open the directory `ddg` as vault to edit and preview locally
6. `npx quartz sync` to push to git
	- to continue work: retrieve current files from the repo without losing your current local file progress: `git fetch git@github.com:wormyrocks/ddg`. [more info here](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository)

non-git workflow:
use [noteshub](https://about.noteshub.app/)?
use [pull](https://github.com/apps/pull)?

----
# todo
last updated 8/25/2024 
- [ ] domain
- [ ] themes?
- [ ] general organization / hierarchy 
- [ ] figure out/create css page templates 
- [ ] do better pdf previews 
- [ ] figure out media content slides 
- [ ] add year/season attribution to content posted 


----
# random notes

base url is stored in `quartz.config.ts`  
`ctrl+o` searches for a file  
`ctrl+p` searches for a command  
`ctrl+e` switches between edit and view modes  
`ctrl+,` opens preferences  

**in markdown, the most annoying thing to remember is that you need to use two spaces before it will insert a new line lol**

----

## adding a new page

creating a new page requires adding frontmatter. the file should be created in `content/` and should be created from `template/default.md`. so in obsidian this looks like:
* `Ctrl-P` -> `Create New Note`
	* make sure the file shows up in the `content/` folder, this should be on by default but might not stick. i am overriding gitignore to add `.obisidan/app.json`, and `.obsidian/templates.json` hopefully this does not cause problems in the future
* `Ctrl-P` -> `Templates: Insert template` -> `default`
* then you should have a new page that lets you enter a title, tags, and mark it as a draft.
	* not quite sure how marking something as a draft behaves. will investigate with [[draft test]].

----

## subpages / folder pages

if you just want to throw a bunch of files into a directory and have a base site that links to all of them, put a file called `index.md` at the root of the directory, add frontmatter (which lets you set the title), and leave the rest of it blank.
then, the other files inside the subpage
this could be useful if, for instance, we wanted a top-level page that links to all the audio files, but unfortunately it only seems to work for markdown.
for example: [[content/technical/index|index]]

----

## embeds

you should be able to drag and drop pictures into obsidian and if all goes right it should get copied into `/media`.

for youtube stuff, it looks like you can embed with this syntax:

```ts
![](https://www.youtube.com/watch?v=7YdgvjE7dA0)
```

(see [[test#a video]])

obsidian supports in-line HTML which means embed code can be copied from a site like soundcloud or bandcamp and will work when pasted directly into a document.

here's what soundcloud's embed code (found under share -> embed -> code) looks like: 

```html
<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/1511945842&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/dannn" title="DANNN​" target="_blank" style="color: #cccccc; text-decoration: none;">DANNN​</a> · <a href="https://soundcloud.com/dannn/spectral" title="Spectral" target="_blank" style="color: #cccccc; text-decoration: none;">Spectral</a></div>
```

(see [[test#Embedded music]])

---

## custom CSS

it's possible to add specific css to pages by adding `[data-slug=""]` to  `quartz/styles/custom.scss`. 

for example, if you want to change the color of the text on link hovers on *this* page, AND override default CSS stylings:

`quartz/styles/custom.scss`

```ts
[data-slug="technical/how-to"] a:hover { color: purple !important; } 
// turns the hover color on a page purple.
```

---

## 