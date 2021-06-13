---
title: DBpedia Neural Extraction Framework
---

# Towards a neural extraction framework

## Project description
### Background
Every Wikipedia article links to a number of other articles. In DBpedia, we keep track of these links through the *dbo:wikiPageWikiLink* property. Thanks to them, we know that the [:Berlin_Wall](https://dbpedia.org/resource/Berlin_Wall) entity is semantically connected to 299 base entities. This project is funded by [Google Summer of Code 2021](https://summerofcode.withgoogle.com/projects/#5166362588086272).
### Problem
However, only 9 out of 299 base entities are linked from [:Berlin_Wall](https://dbpedia.org/resource/Berlin_Wall) via also another predicate. This suggests that in the large majority of cases, it is not clear what kind of relationship exists between the entities. In other words, DBpedia does not know what specific RDF predicate links the subject (in our case, [:Berlin_Wall](https://dbpedia.org/resource/Berlin_Wall)) to any of the objects above.
Currently, such relationships are extracted from tables and the infobox (usually found top right of a Wikipedia article) via the Extraction Framework. Instead of extracting RDF triples from semi-structured data only, we want to leverage information found in the entirety of a Wikipedia article, including page text.
### Goals
The goal of this project is to develop a framework for predicate resolution of wiki links among entities. I choose to focus on a specific kind of relationship: ***Causality***. The direct cause-effect between events, e.g., from the text
> The Peaceful Revolution (German: Friedliche Revolution) was the process of sociopolitical change that led to the opening of East Germany’s borders with the west, the end of the Socialist Unity Party of Germany (SED) in the German Democratic Republic (GDR or East Germany) and the transition to a parliamentary democracy, which enabled the reunification of Germany in October 1990.

**Expecting results :Peaceful_Revolution  –––dbo:effect––> :German_reunification**
