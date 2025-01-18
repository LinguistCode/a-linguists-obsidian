<header>

![header](https://i.imgur.com/ptYxyf2.jpeg)

# A Linguist's Obsidian Setup

_Here are the css snippets and the templates I use in Obsidian, as a linguist._

</header>

## Workflow

In order to make use of the snippets and templates, you need to know about my setup.

### Obsidian

My whole work setup revolves around [Obsidian](https://obsidian.md/).  I use a variety of plugins but the following are central:
- [Calendar](https://github.com/liamcain/obsidian-calendar-plugin) on [Obsidian Plugins page](https://obsidian.md/plugins?id=calendar)
- [Commander](https://github.com/phibr0/obsidian-commander) on [Obsidian Plugins page](https://obsidian.md/plugins?id=cmdr)
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview) on [Obsidian Plugins page](https://obsidian.md/plugins?id=dataview)
- [Folder Note by Lost Paul](https://github.com/LostPaul/obsidian-folder-notes) on [Obsidian Plugins page](https://obsidian.md/plugins?id=folder-notes)
- [Hover Editor](https://github.com/nothingislost/obsidian-hover-editor) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-hover-editor)
- [Interlinear Glossing](https://github.com/Mijyuoon/obsidian-ling-gloss) on [Obsidian Plugins page](https://obsidian.md/plugins?id=ling-gloss)
- [Kanban](https://github.com/mgmeyers/obsidian-kanban) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-kanban)
- [List Callouts](https://github.com/mgmeyers/obsidian-list-callouts) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-list-callouts)
- [Pandoc Plugin](https://github.com/OliverBalfour/obsidian-pandoc) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-pandoc)
- [Pandoc Reference List](https://github.com/mgmeyers/obsidian-pandoc-reference-list) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-pandoc-reference-list)
- [Tag Wrangler](https://github.com/pjeby/tag-wrangler) on [Obsidian Plugins page](https://obsidian.md/plugins?id=tag-wrangler)
- [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-tasks-plugin)
- [Telegram Sync](https://github.com/soberhacker/obsidian-telegram-sync) on [Obsidian Plugins page](https://obsidian.md/plugins?id=telegram-sync)
- [Templater](https://github.com/SilentVoid13/Templater) on [Obsidian Plugins page](https://obsidian.md/plugins?id=templater-obsidian)
- [Zotero Integration](https://github.com/mgmeyers/obsidian-zotero-integration) on [Obsidian Plugins page](https://obsidian.md/plugins?id=obsidian-zotero-desktop-connector)

### Zotero

I use Zotero for all of my reading. I annotate everything I read in Zotero and then I import the annotations into Obsidian. I use a few plugin with Zotero :

- [BetterBibTex](https://retorque.re/zotero-better-bibtex/)
- [DOI Manager](https://github.com/bwiernik/zotero-shortdoi)
- [Scite Zotero Plugin](https://github.com/scitedotai/scite-zotero-plugin)
- [Zotero OCR](https://github.com/UB-Mannheim/zotero-ocr)
- [Zotero Reading List](https://github.com/Dominic-DallOsto/zotero-reading-list)

### Telegram 

On top of messaging, I use the Telegram App on my phone to send notes directly to my Obsidian Vault. You will find the templates I use to import the messages below. 


## Obsidian CSS Snippets

- Litnotes -> Styling options for my literature notes, to format what I bring from Zotero
- authornotes -> Styling options for the recap note that display every publication by a given author and relevant information
- banners -> Tweaks for [SIRvb's](https://publish.obsidian.md/slrvb-docs/ITS+Theme/Image+Adjustments) banners, i.e. the possibility for them to fade and take the whole width of the note
- clippingstyles -> Styling options for the three types of "clippings" I have in my Vault
- dailynote -> Styling options for my dailynotes. Includes special callouts. 
- displaytitle -> cssclass to enable the inline display of a note's title above the properties (which is turned off in my Vault)
- firstletter -> cssclass to enable a stylized drop-cap
- headersindent -> cssclass to enable the gradual indentation of headers in a note
- extracallouts -> special callout styles to be used everywhere
- widernotes -> different cssclasses to change the width of individual notes
- justifiednotes -> cssclass to enable justified text
- niceblockquotes -> a tweak and edit of [AppolloGoneRogue's snippet](https://forum.obsidian.md/t/how-to-achieve-css-code-snippets/8474/244?u) to make it into a toggleable cssclass more fitting to my vault


## Obsidian Templates

### Periodic Notes 
- Daily Notes Template -> for daily notes
- Monthly Recap Template -> for monthly notes
- Yearly Recap Template -> for yearly notes

### Zotero Literature Notes
Some parts of the code I use were taken from [FeralFlora's template](https://gist.github.com/FeralFlora/78f494c1862ce4457cef28d9d9ba5a01). 
All of my zotero templates gather the following information and store it in the note's frontmatter : creator names, date, short title displayed as aliases, citekey, title, tags, publication year, authors, importation date, item type

- Zotero Callout Template -> Orders the annotations into coloured callouts that correspond to the colour of the annotation in Zotero and its type (underline, highlight, image), with a link to the annotation formated like (year:page) and the comment associated with the annotation
- Zotero Linear Template -> The annotations are imported in the order in which the appear in Zotero, using blockquotes and the word "quote" highlighted or underlined in the relevant colour. Images are imported in callouts. Links to the annotations are also formated like (year:page).
- Zotero Grouped Template -> A modification of FeralFlora's template that fits my use and orders the annotation by color rather than lineraly.

### Telegram Sync Templates

<footer>
---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/github-pages) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
