# Sitegeist - Neos Best Practices

The following best practices and rules are used by sitegeist internally for our Neos projects. They combine the learnings we accumulated by creating medium and large scale Neos projects. *This rules are not mandatory for anyone outside of sitegeist and may even be a bad idea for smaller projects.*

The recommendation we are giving here do not mean that things cannot be done differently, there are valid reasons to deviate from those guidelines. Deviations MUST be coordinated with the project leads and SHOULD be documented.

These rules apply to all new projects, all refactorings and new features that are implemented in existing projects. For bugfixes and minor adjustments it is up to the developer to decide whether it is possible to improve the compliance of the project to the best practices.

## Rules 

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

### General

1. The Neos Best Practices as described in https://www.neos.io/blog/neos-best-practices-1-0.html MUST be respected.

1. All projects MUST contain a Makefile and implement the cli-commands `make install`, `make build`, `make up` and `make down`. It is RECOMMENDED to also implement `make watch`, `make lint`, `make test`, `make cleanup` and `make deploy-*`.

1. All projects MUST contain a Readme with a short description and the urls for the various stages and all essential tasks that are not automated via `make`.

1. Projects SHOULD be started with the [Sitegeist Neos Base Distribution](https://github.com/sitegeist/sitegeist-neos-base-distribution)

1. For a better overview of the settings made, it is RECOMMENDED to place larger sections in separate files corresponding to the respective topic, e.g. `Settings.Monocle.yaml` or `Settings.Search.yaml`.

1. Each project MUST provide an automated way to fetch the current data from the server [Sitegeist.MagicWand](https://github.com/sitegeist/Sitegeist.MagicWand) is RECOMMENDED for this as dev dependency.

1. Each project MUST provide an automated way to deploy the current state to the server. Deployer is a RECOMMENDED tool for this but other solutions are also valid.

1. The different environments of a project MUST be easily distinguishable. This MAY be achieved with visual hints (CSS) or a title prefix like "DEV" or "Stage" for non-live environments.

### NodeTypes

1. All NodeTypes SHOULD be in the project Namespace especially `Neos.Neos:Page` and `Neos.Neos:Shortcut` SHOULD be used indirectly as superTypes for project nodeTypes to have full control over all constraints.

1. NodeTypes SHOULD use reasonable groups, icons and labels to distinguish the elements from each other (e.g. structural vs content elements). Content elements that are allowed to exist in the tree but should not be available to the user MUST NOT be visible. This MAY be achieved via constraint (RECOMMENDED), policy, non-existent groups or by declaring legacy-nodetypes abstract.

1. It is RECOMMENDED to use a dedicated NodeType for the site-node. This allows to add site-settings to the inspector, control the rendering and define important documents as autocreated childnodes.

1. Nodes necessary for proper rendering like 404 documents or navigation collections SHOULD be defined as autocreated childNodes with a dedicated NodeType.

1. The configurations for inline editor options MUST be centralized for a consistent editing experience and a limited number of variants. This MAY be done by using Mixins or by using the [Sitegeist.Silhouettes](https://github.com/sitegeist/Sitegeist.Silhouettes) package.

1. If possible, models SHOULD be based on the data models provided by schema.org. This allows you to stick to common conventions and makes it easy for you to render JSON-LD tags used by search engines.

1. For classification and aggregation of nodes the package [Sitegeist.Taxonomy](https://github.com/sitegeist/Sitegeist.Taxonomy) SHOULD be used.

### Fusion

1. Presentation and integration SHOULD be handled separately in different folders.

1. Integration components SHOULD NOT contain markup.

1. Presentation components MUST NOT use domain entities and information.

1. The API of presentational components MUST describe the expected behavior. Especially the `inBackend` flag MUST NOT be used. It is RECOMMENDED to use behavior describing flags like `suppressLink` instead.

1. Presentation components MUST be tested in isolation from the integration. It is RECOMMENDED to use the  [Sitegeist.Monocle](https://github.com/sitegeist/Sitegeist.Monocle) styleguide to do so.

1. To mock complex data structures for the styleguide the `*.Fixtures` namespace is RECOMMENDED. Components that only need sections of larger Fixtures MAY use @process-rules for partial access.

1. Presentational components that cannot be previewed standalone MAY provide a `*.Preview` prototype.

### Frontend

1. All frontend components SHOULD be tested in isolation AND on a dummy page in the styleguide. Those dummy pages in the styleguide are useful for acceptance (customer and pm) and help to spot component-margin issues.

1. It MUST be ensured that visitors get fresh css and js resources after each deployment. The [Sitegeist.KlarSchiff](https://github.com/sitegeist/Sitegeist.KlarSchiff) package is the RECOMMENDED way for this.

1. Image rendering SHOULD be implemented with [Sitegeist.Kaleidoscope - Responsive Images](https://github.com/sitegeist/Sitegeist.Kaleidoscope) and [Sitegeist.Lazybones - Lazy Loading](https://github.com/sitegeist/Sitegeist.Lazybones) from the start. While the responsive behavior MAY be defined later or not at all it is costly and error prone to integrate these packages later.

## Contribution

Please send us pull requests (if you want to suggest a concrete rule) or open issues if you have a suggestion but no clear wording yet. Make sure to look for duplicates before creating a new issue/pr.

- Rules MUST use English language
- Rules MUST be short, precise and verifiable
- Rules MUST apply to the majority of Neos projects
