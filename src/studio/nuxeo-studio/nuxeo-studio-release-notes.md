---
title: Nuxeo Studio Release Notes
description: Discover changes brought in our recent Nuxeo Studio updates.
review:
    comment: ''
    date: ''
    status: ok
toc: true
tree_item_index: 730
---

Discover the changes we brought in our latest Nuxeo Studio updates.


## January 7, 2019
{{{multiexcerpt 'summary-v3-3-1' page='2019-01-07-studio-3-3-1'}}}

## Upcoming Changes

### Studio Designer Interface Improvements

The layouts and UI menus in Studio Designer have been merged into a single one. This provides greater consistency with Studio modeler and an easier user experience.

Menus change as following:
- `Layouts` are moved into a menu option and closed by default

![Layouts Change]({{file name='layouts-menu-change.png' page='2019-01-07-studio-3-3-1'}})

- `Document Pages` entry is renamed as `Tabs`

![Document Pages Change]({{file name='document-pages-change.png' page='2019-01-07-studio-3-3-1'}})

- `Left Menu Items` and `Main Menu Pages` are merged into a dedicated `Drawer` menu

![Left Menu Items Change]({{file name='left-menu-items-change.png' page='2019-01-07-studio-3-3-1'}})

## Released Changes

### Noteworthy Improvements and Bugfixes

- Tags can be pushed using Git access ([NXS-4882](https://jira.nuxeo.com/browse/NXS-4882)).
- A warning is given when you create a query using the deprecated trash management behavior in content views ([NXS-5054](https://jira.nuxeo.com/browse/NXS-5054)).

[More information about bugs fixed since last release notes](https://jira.nuxeo.com/issues/?jql=project %3D NXS AND fixVersion IN %28'3.3.0','3.3.1'%29) is available in our bug tracking tool.

* * *

## Previous Release Notes

| Release Date  | Summary  |
|---|---|
|[December 12, 2018]({{page page='2018-12-12-studio-3-2-0'}})|  Faster layouts configuration.|
| [November 26, 2018]({{page page='2018-11-26-studio-3-1-0'}})| Firefox support for Studio Designer, performance improvements, drag and drop schema properties in Studio Designer and information about your subscription status.|
| [October 29, 2018]({{page page='2018-10-29-studio-73-24'}})| Develop faster with Git access and Quick Switcher, JSF to Web UI migration early access release.|
| [September 17, 2018]({{page page='2018-06-11-studio-73-21-1'}})  | Introducing Git access for Studio Designer.|
| [June 11, 2018]({{page page='2018-06-11-studio-73-14'}})| Application definition supports private package selection, introducing token management for enhanced security.|
|  [May 28, 2018]({{page page='2018-05-28-studio-73-13'}})| Selecting dependencies makes their content automatically available for use in Studio. There are several other usability improvements in Studio Designer that make life easier.|
| [April 17, 2018]({{page page='2018-04-17-studio-73-11-1'}})| This release makes it easier to create a document type when using Web UI.|
| [April 2, 2018]({{page page='2018-04-02-studio-73-9'}})| You can now configure your project as a real application containing dependencies on any public addon without having to make a dedicated custom bundle. This release also brings improvements to our Maven integration.|
| [March 5, 2018]({{page page='2018-03-05-studio-73-8'}})|A REST API to trigger Studio releases, a revamped editor for page providers results and the ability to declare constraints for workflow variables and node variables.|
| [February 7, 2018]({{page page='2018-03-05-studio-73-8'}})|Studio now handles lost sessions gracefully, and provides advanced configuration patterns for JSF UI layouts' widgets.|
| [January 3, 2018]({{page page='2018-01-03-studio-73-4'}})| Studio will now show your work in progress changes, commits to push or pull. It can be used to monitor your work status, and also to review configuration changes made by others.|

## We Want Your Feedback!
Feel free to let us know how we could [make Studio better](https://portal.prodpad.com/eb062eda-6d54-11e7-8513-22000a2145da) for you!

{{! /multiexcerpt}}