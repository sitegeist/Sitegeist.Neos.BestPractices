# Sitegeist - Neos Best Practices

The following best practices and rules are used by sitegeist internally for our Neos projects. They combine the learnings we accumulated by creating medium and large scale Neos projects. *This rules are not mandatory for anyone outside of sitegeist and may even be a bad idea for smaller projects.*

The recommendation we are giving here do not mean that things cannot be done differently, there are valid reasons to deviate from those guidelines. Deviations MUST be coordinated with the project leads and SHOULD be documented.

These rules apply to all new projects, all refactorings and new features that are implemented in existing projects. For bugfixes and minor adjustments it is up to the developer to decide whether it is possible to improve the compliance of the project to the best practices.

## Rules 

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

### General

1. The Neos Best Practices as described in https://www.neos.io/blog/neos-best-practices-1-0.html 
   MUST be respected.
   
2. If possible, models SHOULD be based on the data models provided by schema.org. This allows you to stick to common conventions and makes it easy for you to render JSON-LD tags used by search engines.   

2. For a better overview of the settings made, it is RECOMMENDED to place larger sections in separate files corresponding to the respective topic, e.g. 'Settings.Monocle.yaml' or 'Settings.Search.yaml'.

### NodeTypes

1. It is RECOMMENDED to use a dedicated NodeType for the site-node. This allows to add site-settings to the inspector, control the rendering and define important documents as autocreated childnodes.

2. NodeTypes SHOULD use reasonable groups, icons and labels to distinguish the elements from each other (e.g. structural vs content elements). Content elements that are allowed to exist in the tree but should not be available to the user MUST NOT be visible. This MAY be achieved via constraint (RECOMMENDED), policy, non-existent groups or by declaring legacy-nodetypes abstract.

### Fusion

### Frontend

## Contribution

Please send us pull requests (if you want to suggest a concrete rule) or open issues if you have a suggestion but no clear wording yet. Make sure to look for duplicates before creating a new issue/pr.

- Rules MUST use English language
- Rules MUST be short, precise and verifiable
- Rules MUST apply to the majority of Neos projects
