---
title: 'Is it Possible to Export a Studio Project in Eclipse?'
description: Discover what we recommend instead of exporting your Studio Project in Eclipse.
review:
  comment: ''
  date: ''
  status: ok
toc: true
tree_item_index: 1300
---

{{! excerpt}}
From your instructions, Nuxeo Studio generates XML configurations. The plugin you can download from Nuxeo Studio is a strict set of XML files and pictures.
{{! /excerpt}}
To have a closer look: rename the downloaded JAR and unzip it. You can find the sources of your project.

Technically, nothing prevents you from importing these files in Eclipse, modify them and commit changes in your own source repository.

**Yet, we do not recommend it.**

There is no reverse path:

- You will **definitively** lose the ability to maintain your project in Studio. For example, you will no longer be able to configure any feature in a more recent version, or use drag and drop to modify an automation chain.
- You will lose the ease of maintenance. Indeed, to upgrade a plugin made with Studio, all you need is to change the version of the distribution of your project. Nuxeo Studio generates the XML according to your target application version.

If you consider switching your project to Eclipse because:

**You are blocked in Studio and cannot do something you want:**

- Try contributing an external declaration in the [Advanced Settings]({{page page='advanced-settings'}}).
- Submit your problem through the Help Request form or to your Nuxeo Support Team. We value your feedback, we build the Studio roadmap priorities around it!

**You want to export the code to maintain configuration sources more easily:**

- Take a look at the [Branch Management]({{page page='branch-management'}}). You can commit your changes, track them and create tagged versions of your project, as well as manage several branches of the configuration.