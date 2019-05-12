# dat-pkg
Draft specification of decentralized package registry and manager based on the Dat protocol

This is based on a series of tweets I just made. It needs to be implemented! Make pull requests to help make that happen.

**License:** figuring that out!

## spec

> Anyone actually working on a decentralized Dat-based package manager?
>
> 1. 1 Package <-> 1 Dat
> 2. Human-readable+unique package names OPTIONAL (& namespaced)
> 3. Each namespace managed in single-writer Dat with name pointers to pkgs
> 4. A registry (also a Dat?) points to namespaces
>
> Registry and namespace dats, although single writer, would have http mechanisms for accepting updates to their listings from package authors.
>
> One other detail is what happens if a pkg dat's update credentials get lost - a registry entry can be updated to point to a new dat, but clients will only accept it if the dat history matches. Because dat uses an append-only log, verification is straightforward!

Other notes:

- A subdirectory for the actual package contents, and a subdirectory for version pointers
- Each version pointer file can contain:
    - The version in the dat history where the content exists (this is **required** and cannot be changed once added)
    - A git repo address (optional and can be changed)
    - A git commit hash (**required if/only if git repo address is provided**, and can be changed... if you really have to!!)
    - A build step command, if applicable for the git repo source
    - A boolean, is this version deprecated? If ever set true, it can't be set false again. (We can't unpublish versions because the history is immutable, so this is what we have instead. Long story short.. don't publish sensitive data!)
- The git repo, commit hash and build step can be used to verify the integrity of published package versions against published source code in the dat repo.
    - Registries can use this to verify package integrity
    - Users can also run the verification locally (although this wouldn't be a typically required step for installing packages, since it could take a very long time for a large number of packages)
