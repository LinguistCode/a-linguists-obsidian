---
icon: IbAcademicBook
aliases:
- "{%- if creators -%}
        {{creators[0].lastName or creators[0].name }}
        {%- if creators|length == 2 %} & {{creators[1].lastName or creators[1].name}}{% endif -%}
        {%- if creators|length > 2 %} et al.{% endif -%}
    {%- endif -%}
    {%- if date %} ({{date | format("YYYY")}}){% endif -%} 
    {%- if shortTitle %} {{shortTitle | safe}} {%- else %} {{title | safe}} {%- endif -%}" {% if itemType == "bookSection" %}
book-title: "{{bookTitle}}"{% endif %}
category: literaturenote
citekey: {{citekey}}
title: "{{title}}"
tags: {% if allTags %}{{allTags}}{% endif %}
pub-year: {{date | format("YYYY")}}
authors: {{authors}}
status: read
dateread: {{exportDate | format("YYYY-MM-DD")}}
zot-item-type:  {{itemType}}
{%- if notes.length > 0 -%}  
{%- set longShortCutoff = 20 -%}  
{%- set shortnotes = [] -%}  
{%- set longnotes = [] -%}  
{%- for note in notes -%}  
{%- if note.note | wordcount <= longShortCutoff -%}  
{%- set shortnotes = (shortnotes.push(note.note), shortnotes) -%}  
{%- else -%}  
{%- set longnotes = (longnotes.push(note), longnotes) -%}  
{%- endif -%}{%- endfor -%}{%- endif -%}  
{%- for comment in shortnotes %}  
{%- if comment and loop.first %}  
comments:  
{% endif -%}
- "{{comment|replace('"',"'")| replace("\n"," ")}}"{% endfor %}
cssclass: litnote
---

<span class="zheader"> {{title}} </span>

> [!cite]- 
> {{bibliography}}

>[!zoterometa]- Literature Metadata
>
>**Related**: {% for relation in relations %} {{relation.creators[0].lastName}} *{{relation.title}}* {% if not loop.last  %}{% if not loop.first  %}; {% endif%}{% endif%} {% endfor %}
> 
>**Authors**: {% for a in creators %} [[Knowledge base/Authors/{{a.firstName}} {{a.lastName}}|{{a.firstName}} {{a.lastName}}]]{% if not loop.last %}, {% endif %}{% endfor %}
> 
> {% if tags %}**Tags**: {% for t in tags %}#{{t.tag | replace(r/\s+/g, "-")}}{% if not loop.last %}, {% endif %}{% endfor %}{% endif %}
> **Title**: {{title}}  
> **Year**: {{date | format("YYYY")}}   
> **Citekey**: {{citekey}} {%- if itemType %}  
> **Type of Item**: {{itemType}}{%- endif %}{%- if itemType == "journalArticle" %}  
> **Journal**: *{{publicationTitle}}* {%- endif %}{%- if volume %}  
> **Volume**: {{volume}} {%- endif %}{%- if issue %}  
> **Issue**: {{issue}} {%- endif %}{%- if itemType == "bookSection" %}  
> **Book**: {{publicationTitle}} {%- endif %}{%- if publisher %}  
> **Publisher**: {{publisher}} {%- endif %}{%- if place %}  
> **Location**: {{place}} {%- endif %}}{%- if DOI %}  
> **DOI**: {{DOI}} {%- endif %}{%- if ISBN %}  
> **ISBN**: {{ISBN}} {%- endif %}    
> ---
> **Collections**:: {% for collection in collections %}[[{{collection.name}}]]{% if not loop.last %}, {% endif %}{% endfor -%}
{%- set readingSpeed = 220 %}
{%- set wordsPerPage = 360 %}
{%- if pages %}
    {%- set pageRegex = r/(\d+)\-(\d+)/ %}
    {%- set splitPages = pageRegex.test(pages) %}
    {%- if splitPages %}
        {%- set pageMatch = pageRegex.exec(pages) %}
        {%- set firstPage = pageMatch[1] %}
        {%- set pageCount = pageMatch[2] - pageMatch[1] %}
    {%- else %}
        {%- set pageCount = pages %}
    {%- endif %}
{%- elif numPages %}
    {%- set pageCount = numPages %}
{%- else %}
	{%- set pageCount = 0 %}
{% endif -%}
{%- if firstPage %}
>
> **First-page**:: {{firstPage}}
{%- endif -%}
{%- if pageCount > 0 -%}
    {%- set readingTime = ((pageCount* wordsPerPage)/readingSpeed)/60 %}
> 
> **Page-count**:: {{pageCount}}
> 
> **Reading-time**:: {% if readingTime < 1 %}{{(readingTime * 60) | round + " minutes"}}{% else %}{{readingTime | round(3) + " hours"}}{% endif %}{% endif %}

> [!link]- Links :  [**Zotero**]({{desktopURI}}){% if DOI %} | [**DOI**](https://doi.org/{{DOI}}){% endif %}
> {%- for attachment in attachments | filterby("path", "endswith", ".pdf") %}
>  [{{attachment.title}}](file://{{attachment.path | replace(" ", "%20")}})  {%- endfor -%}.
>  

> [!abstract]-
> {%- if abstractNote %}
> {{abstractNote}}
> {%- endif -%}.
> 

---

# :RiListView: Summary
{% persist "notes" -%}  
{%- if isFirstImport %}


# :RiStickyNoteFill: Notes
{%- set headingRegex = r/^#+/ -%}
{%- set titleRegex = r/^#+.*/ -%}
{%- set lineRegex = r/^.*$/m %}
{%- if longnotes.length > 0 -%}
{%- for n in longnotes -%}
{%- if n and loop.first %}

> [!note|bg-c-yellow]- Zotero notes ({{longnotes.length}})
> <small>Notes longer than {{longShortCutoff}} words.</small>
{%- endif %}
>> [!example|bg-c-orange]- Note {{loop.index}} |{%- if headingRegex.test(n.note) == true %}[{{n.note | replace(n.note,titleRegex.exec(n.note))|replace(headingRegex,"")}}]({{n.uri}}){% else %} [{{lineRegex.exec(n.note | truncate(30))}}]({{n.uri}})
>> {% endif %}
>> {{n.note | replace("\n", "\n>> ")| replace(titleRegex, "")}}{% if n.tags.length > 0 %}
>>
>> Tags:{% for t in n.tags %} #{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}{% endif -%}{%- if not loop.last %}
>{%- endif -%}
{%- endfor -%}{%- endif %}


{% endif %}{% endpersist %}

# :FasBookOpenReader: Annotations

>[!thinkaside|right title]- Color Code
><span style="background:rgba(240, 200, 0, 0.2)">Yellow : contenu intéréssant / à réutiliser </span>
><span style="background:rgba(3, 135, 102, 0.2)">Green : Les idées que m'évoquent certains passages. </span>
><span style="background:rgba(163, 67, 31, 0.2)">Red : contenu capital</span>
><span style="background:rgba(5, 117, 197, 0.2)">Blue : contenu bibliographique (renvoi vers un autre auteur / reference)</span>
><span style="background:rgba(240, 107, 5, 0.2)">Orange : intéréssant mais annexe</span>
><span style="background:rgba(74, 82, 199, 0.2)">Violet : contenu théorique, notion, thème à réutiliser </span>
> <span style="background:rgba(136, 49, 204, 0.2)">Magenta : Pas d'accord, j'ai des contre-arguments OU je ne comprends pas</span>
><span style="background:rgba(140, 140, 140, 0.12)">Gris : Me fait penser à autre chose, pas vraiment en lien avec le passage ou non pertinent pour la these directement.</span>

{%- macro calloutHeader(type, color, colorCategory) -%}
{%- if type == "highlight" -%}>[!zotquote|{{colorCategory}}] :TiInfoHexagon: Quote
{%- endif -%}
{%- if type == "underline" -%}>[!zotquote|{{colorCategory}}] :FiUnderline: Quote {%- endif -%}
{%- if type == "text" -%}>[!zotquote|text] :IbText2: On-file annotation
{%- endif -%}  

{%- endmacro -%}

{% persist "annotations" %}
{% set newAnnotations = annotations | filterby("date", "dateafter", lastImportDate) %}
{% if newAnnotations.length > 0 %}

### Imported on: {{importDate | format("YYYY-MM-DD")}} at {{importDate | format("HH:mm")}}

{% for a in newAnnotations %}
{%- set citationLink = '[('~ creators[0].lastName ~' '~ date | format("YYYY")~':'~ a.pageLabel ~ ')](' ~ a.desktopURI ~ ')' %}

{%- if a.imageRelativePath %}
>[!picture|{{a.colorCategory}}]+ Image {{citationLink}}
>> ![[{{a.imageRelativePath}}]]
{% if a.hashTags %} >> {{a.hashTags}} {% endif %} 
{% if a.comment %} > :IbArrowThickRight: **{{a.comment}}**  {% endif %}
{% endif %}
{% if a.type == "underline" or a.type == "highlight" or a.type == "text" %}
{{calloutHeader(a.type, a.color, a.colorCategory)}}
> "{{a.annotatedText}}" {{citationLink}} 
{% if a.comment %}> :IbArrowThickRight: **{{a.comment}}**  {% endif %}{% if a.hashTags %}>Tags: {{a.hashTags}}{% endif %}
{% endif %}{% endfor %}{% endif %}{% endpersist %}