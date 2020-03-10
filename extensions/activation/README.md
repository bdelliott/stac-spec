# Planet Asset Activation Extension Specification

- **Title: Activation**
- **Identifier: activation**
- **Field Name Prefix: pla**
- **Scope: Item**
- **Extension [Maturity Classification](../README.md#extension-maturity): Proposal**

This document explains the fields of the Planet asset activation  (`activation`) extension to a STAC item.

The field names defined herein should be added as fields on assets listed in an item's `Assets` map.

Planet's imagery assets are not typically pre-generated.  This extension provides a means to "activate" imagery so that
it will be generated and made available to users.  Once generated, the `href` field from the base asset definition will be populated with a valid URL to retrieve the asset.

An asset may have one of the following status values:

| Status       | Description                                           |
| ------        | -----------                                          |
| `inactive`   | Asset is unavailable, needs activation                |
| `activating` | Asset activation is in progress                       |
| `active`     | Asset is active and available for download via `href` |

When an asset is not in an `active` status, the `href` of the asset should return an HTTP 409 (conflict) if an attempt is made to access it.

A user may issue an HTTP POST to an asset's activation URL (`pla:activate_href`) to trigger activation.

## Examples
- [Sample](examples/sample.json)

## Schema
- [JSON Schema](json-schema/schema.json)

## Item Asset fields

| Field Name       | Type                     | Description |
| ---------------- | ------------------------ | ----------- |
| pla:status        | string\|null   | **Required** - Asset activation status |
| pla:activate_href | string \|null   | URL to activate the asset |
