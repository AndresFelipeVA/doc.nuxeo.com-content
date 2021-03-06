---
title: Nuxeo Aspera Upgrade Notes
description: Upgrade notes for Nuxeo Aspera.
tree_item_index: 200
review:
  comment: ''
  date: '2020-09-10'
  status: ok
toc: true
---

{{! excerpt}}
This chapter highlights some major information about upgrade from Nuxeo Aspera Connector 2.x to Nuxeo Aspera Connector 3.0.x.</br>
For a listing of improvements and functional enhancements in version 3.0.x, please see the [release notes]({{page page='nuxeo-aspera-release-notes'}})
{{! /excerpt}}

{{#> callout type='warning'}}
Because of the changes to parameters in the `nuxeo.conf` file as well as code/API changes described below, this release is labeled as a major release.</br>
Transfers that exist in your system **that were started/created with a previous version will not work with this release and attempts to complete them will fail with this release**.</br>
Updating the Connector to version 3.0.0 is not recommended if you have _ongoing_ transfers.
{{/callout}}

## Installation and Configuration

### Changed/Modified Parameters

<div class="table-scroll">
<table class="hover">
<tbody>
<tr>
<th colspan="1">Parameter</th>
<th colspan="1">Modification</th>
<th colspan="1">Reference</th>
</tr>
<tr>
<td colspan="1">`aspera.access.key.id`
`aspera.access.key.secret`
`aspera.download.access.key.id`
`aspera.download.access.key.secret`</td>
<td colspan="1">Fixed existing typo for `acess` in these parameters</td>
<td colspan="1">[NXP-28399](https://jira.nuxeo.com/browse/NXP-28399)</td>
</tr>
<tr>
<td colspan="1">`nuxeo.s3storage.useDirectUpload = true`</td>
<td colspan="1">Value no longer necessary for the Nuxeo Aspera Connector (keep if used for other Nuxeo features) </td>
<td colspan="1">[NXP-29548](https://jira.nuxeo.com/browse/NXP-29548)</td>
</tr>
<td colspan="1">`nuxeo.s3storage.transient.roleArn`</td>
<td colspan="1">Value no longer necessary for the Nuxeo Aspera Connector (keep if used for other Nuxeo features)</td>
<td colspan="1">[NXP-29548](https://jira.nuxeo.com/browse/NXP-29548)</td>
</tr>
</tbody>
</table>
</div>

### Requirements

- Aspera Desktop Client - [latest version]
- Nuxeo Server LTS 2019 (10.10, HF 31, at least) with access to AWS S3 Storage along with the [Amazon S3 Online Storage plugin](https://connect.nuxeo.com/nuxeo/site/marketplace/package/amazon-s3-online-storage?version=1.9.12)
- IBM Aspera on Cloud Subscription (see note above about Aspera self-hosted)

## Code/Element Changes

### Transfer Status

`updateTransferStatuses` deprecated - use `syncTransfer`(CoreSession, String) instead.

See [NXP-29425](https://jira.nuxeo.com/browse/NXP-29425).

### Transfer 'tab' Behavior

- `nuxeo-aspera-upload-page` element: Replaced `aspera-tab-update` event by `aspera-page-update` event.
- `nuxeo-aspera-page` element: changed `selectedtab` property into `selectedPage` property.

See [NXP-29130](https://jira.nuxeo.com/browse/nxp-29130).

### Transfer Page

- On `nuxeo-aspera-transfer-page`: removes property `transferGroups`.

See [NXP-29497](https://jira.nuxeo.com/browse/nxp-29497)

- `nuxeo-aspera-transfer-page` element: removes properties aggregates, params and quickFilters.

See [NXP-29592](https://jira.nuxeo.com/browse/nxp-29592).

- `nuxeo-aspera-transfer-page` element removes properties: `transfers`, `offset` and `isPreviousPageAvailable`

See [NXP-29282](https://jira.nuxeo.com/browse/nxp-29282).

### Storing Message Files

Deprecated `getOrCreateTransferDocument` methods (which was a deprecated Aspera method).

See [NXP-29590](https://jira.nuxeo.com/browse/NXP-29590).

### Workers' Status

Deprecated `bmExecute(Transfer transfer)` and introduces `bmExecute()` instead.

See [NXP-29589](https://jira.nuxeo.com/browse/NXP-29589).

### Transfer Change Event

`transfer-changed` event is deprecated, use `aspera-uploads-refresh` instead.

See [NXP-29302](https://jira.nuxeo.com/browse/nxp-29302).

### Aspera Connect Download

Removes `linkActive` and `download` properties from `nuxeo-aspera-connect`.

See [NXP-28412](https://jira.nuxeo.com/browse/NXP-28412).

### Transfer Complete Event

Removed the `aspera-transfer-complete` event and its listeners. From now on, there is no such event being fired.

See [NXP-29467](https://jira.nuxeo.com/browse/nxp-29467).

### Transfer Edit

Removed `nuxeo-aspera-upload-edit-dialog` element.

See [NXP-28207](https://jira.nuxeo.com/browse/nxp-28207).

## Complementary Information

- [Release notes for 3.0.0](https://doc.nuxeo.com/nxdoc/nuxeo-aspera-connector/nuxeo-aspera-release-notes/)
- [Nuxeo Aspera Connector](https://doc.nuxeo.com/nxdoc/nuxeo-aspera-connector/)
