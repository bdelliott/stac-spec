# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased]


## [v0.6.0-rc2] - 2018-10-25

### Fixed
- Reorganized and cleaned up repository
- Fixed examples throughout

### Added
- **Changelog**: This changelog added
- **Collections added**: Collections are a type of Catalog with additional fields, such as provider and license. Items must belong to a single Collection.
- **Extension maturity**: Protocol for providing maturity classification for extensions based on stability and implementations.
- **Commons extension**: The previous 'Collections' extension is now the 'Commons' extension and allows an Item to inherit properties from it's Collection.
- **Datetime-range extension**: Extension for providing start and end datetimes.
- **Scientific extension**: Extension for providings links to scientific publications relating to the data.
- **rel types**: A list of supported 'rel' types are provided for use when specifying links, 'derived_from' and 'license' types added.
- **eo:constellation**: A new field in the EO specification to specify a grouping of platforms.
- **stac_version**: The stac_version field is required on all Catalogs (and Collections)
- **JSON schemas**: Added JSON schemas where they were missing.
- **Single Item extension**: Extension to supply License and Providers for single Items when no collection.
- **UML Diagram**: See STAC-060-uml.pdf
- **Development Process**: See process.md for information on the STAC development process

### Changed
- **Endpoints**: Main catalog endpoint at /stac, search endpoint now at /stac/search
- **eo:bands**: The eo:bands field is now an array rather than a dictionary, and has been moved inside of 'properties' in a STAC Item.
- **Catalog fields**: Catalogs have a smaller number of basic fields: id, stac_version, title (optional), description, and links. The new Collections type contains additional fields.
- **links**: The links fields are now an array rather than a dictionary.
- **properties**: Fields with the data type array or objects are allowed inside the `properties` in a STAC Item.
- **description**: Description fields now allow formatting with CommonMark.
- **assets**: Fields changed names: name to title and mime_type to type.
- **Providers Object in collections**: added a `description` field., renamed `type` to `roles`, change `roles` from string to array and added a `licensor` role.

### Removed:
* **provider**: Provider field in Items got removed. Use Collections instead.
* **license**: License field in Items got removed. Use Collections instead.


## [v0.5.2] - 2018-07-12

Minor bug fixes on 0.5.1 for the schema files. Thanks @francbartoli 


## [v0.5.1] - 2018-07-06

Minor bug fixes from 0.5.1 release

*  [Update openapi / swagger specs for new 'links'](https://github.com/radiantearth/stac-spec/commit/480d4fb02b4a7e880c7ca01320fe2773260ba595)
* [minor fixes on collection extension](https://github.com/radiantearth/stac-spec/pull/124) - thanks @m-mohr 
* [minor cbers example updates](https://github.com/radiantearth/stac-spec/pull/123) - thanks @fredliporace 


## [v0.5.0] - 2018-07-01

The 0.5.0 release of the STAC spec is an iteration forward on the spec, with a number of core improvements. Highlights include:

* **Links is now a dictionary** - This is the most core change done. It aligns the structure with the 'asset' change in 0.5.0, making it easier for clients to look up the link that they want more easily. The schema is updated to this (and actually checks assets better now, thanks @mojodna ) 

* **Transactions Extension** - There is now a transaction extension for the STAC API, thanks to @hgs-msmith and @hgs-trutherford 

* **Collections iterations** @matthewhanson has evolved the collections extension, adding in some namespace type hints on it, and explaining it more clearly.

* **eo:crs to eo:epsg** In the EO profile @matthewhanson brought in a change to use EPSG code, instead of full Well Known Text, to make it easy to reference.

Full list of issues and pull requests at https://github.com/radiantearth/stac-spec/milestone/5?closed=1


## [v0.4.1] - 2018-04-24

A few minor improvements on the release. ([issues](https://github.com/radiantearth/stac-spec/issues?utf8=%E2%9C%93&q=milestone%3A0.4.1+))

* @hgs-msmith got a swagger version of the spec, and made some minor improvements to the openapi version #103 and #102 
* @francbartoli and @m-mohr pointed out some inconsistencies with landsat, so got the openapi updated #106
* @m-mohr pointed out some issues with landsat example, so updated those #105 
* @hgs-trutherford pointed out that the planet example was a bit confusing, so updated it to the EO profile.


## [v0.4.0] - 2018-04-06

The 0.4.0 is the first 'official' release of the SpatioTemporal Asset Catalog (STAC) specification!

It is the result of the [ft. collins sprint](https://github.com/radiantearth/community-sprints/tree/master/03072018-ft-collins-co), the second in person meeting of the STAC community. But it also includes
a number of improvements from remote contributors. 

Highlights include:

* Updates to the core **`Item` JSON specification**, including simplifying to a single datetime, moving thumbnails from 'links' to 'assets', making assets a dictionary for easier lookup and requiring `self` links to be absolute links.

* Alignment of **STAC API** with the new [WFS 3](https://github.com/opengeospatial/WFS_FES/) specification

* Cleanup of the **static catalog** specification for greater clarity around the catalog

* A first cut of an **Earth Observation Profile**, as well as a new collections extension to support it.

* Numerous small improvements and bug fixes.

See the [milestone 0.4.0 in the issue tracker](https://github.com/radiantearth/stac-spec/milestone/3) for the complete lists of improvements. 

Thanks @hgs-msmith, @matthewhanson, @hgs-trutherford, @rouault, @joshfix, @alkamin, @hemphillda, @jeffnaus  and @fredliporace for contributing to the spec directly, and to [everyone](https://github.com/opengeospatial/wfs3hackathon/blob/master/notes/introductions.md#participants) who participated in the [Ft Collins sprint](https://github.com/radiantearth/community-sprints/tree/master/03072018-ft-collins-co) and brought great ideas.


[Unreleased]: https://github.com/radiantearth/stac-spec/compare/master...dev
[v0.6.0-rc2]: https://github.com/radiantearth/stac-spec/compare/v0.5.2...v0.6.0-rc2
[v0.5.2]: https://github.com/radiantearth/stac-spec/compare/v0.5.1...v0.5.2
[v0.5.1]: https://github.com/radiantearth/stac-spec/compare/v0.5.0...v0.5.1
[v0.5.0]: https://github.com/radiantearth/stac-spec/compare/v0.4.1...v0.5.0
[v0.4.1]: https://github.com/radiantearth/stac-spec/compare/v0.4.0...v0.4.1
[v0.4.0]: https://github.com/radiantearth/stac-spec/tree/v0.4.0