# CHANGELOG Template

A fancy template for CHANGELOG files.

## AsciiDoc

### Basic Template

```adoc
= Changelog
:github:
// :gitlab:
:host: https://github.com
:owner: CodeLenny
:project: ...

// :first-commit: [sha]
// :latest-version: ...

ifdef::github[]
:repo-url: https://github.com/{owner}/{project}
:repo-compare: {repo-url}/compare/
:repo-changelog: {repo-url}/blob/master/CHANGELOG.adoc
:compare-split: ...
endif::[]
ifdef::gitlab[]
:repo-url: https://gitlab.com/{owner}/{project}
:repo-compare: {repo-url}/compare/
:compare-split: ...
endif::[]

ifdef::latest-version[]
== link:{repo-compare}{latest-version}{compare-split}HEAD[Unreleased]
endif::[]
ifndef::latest-version[]
ifdef::first-commit[]
== link:{repo-compare}{first-commit}{compare-split}HEAD[Unreleased]
endif::[]
ifndef::first-commit[]
== Unreleased
endif::[]
endif::[]

Initial Release.

### Added
- ...
```

### First Version

- Update `:latest-version:`
- Add after `== Unreleased`:

```adoc
:version: v0.0.1
:version-date: YYYY-MM-DD
:previous-version: {first-commit}
:version-file-url: {repo-url}/tree/{version}
:version-diff-url: {repo-compare}{previous-version}{compare-split}{version}
:version-log-url: {repo-changelog}#{version}---{version-date}

== link:{version-file-url}[{version} - {version-date}]
```

### Later Versions

- Update `:latest-version`
- Use template for first version, but replace `:previous-version: {first-commit}` with an actual version number.
