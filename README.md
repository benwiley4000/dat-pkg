# dat-pkg
Draft specification of decentralized package registry based on the Dat protocol

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

