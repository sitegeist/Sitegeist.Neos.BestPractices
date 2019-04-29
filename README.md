# Sitegeist - Neos Best Practices

The following best practices and rules are used by sitegeist internally for our Neos projects. They combine the learnings we accumulated by creating medium and large scale Neos projects. *This rules are not mandatory for anyone outside of sitegeist and may even be a bad idea for smaller projects.*

The recommendation we are giving here do not mean that things cannot be done differently, there are valid reasons to deviate from those guidelines. Deviations MUST be coordinated with the project leads and SHOULD be documented.

These rules apply to all new projects, all refactorings and new features that are implemented in existing projects. For bugfixes and minor adjustments it is up to the developer to decide whether it is possible to improve the compliance of the project to the best practices.

## Rules 

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119. https://www.ietf.org/rfc/rfc2119.txt

### General

1. The Neos Best Practices as described in https://www.neos.io/blog/neos-best-practices-1-0.html 
   MUST be respected.

### NodeTypes

### Fusion

1. Presentation and integration SHOULD be handled seperately in different folders.

2. Integration components SHOULD NOT contain markup.

3. Presentation components MUST NOT use domain entities and information.

4. The API of presentational components MUST describe the expected behavior. 
   Especially the `inBackend` flag MUST NOT be used. It is RECOMMENDED to use 
   behavior describing flags like `suppressLink` instead.

5. Presentation components MUST be tested in isolation from the integration. It is RECOMMENDED to use the 
   [Sitegeist.Monocle](https://github.com/sitegeist/Sitegeist.Monocle) styleguide to do so.

### Frontend

## Contribution

Please send us pull requests (if you want to suggest a concrete rule) or open issues if you have a suggestion but no clear wording yet. Make sure to look for duplicates before creating a new issue/pr.

- Rules MUST use English language
- Rules MUST be short, precise and verifiable
- Rules MUST apply to the majority of Neos projects
