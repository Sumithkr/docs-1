# ownCloud Documentation

[![Build Status](http://drone.owncloud.com/api/badges/owncloud/docs/status.svg?branch=master)](http://drone.owncloud.com/owncloud/docs)

This project is a port of the ownCloud documentation, that was previously generated using [Sphinx-Doc](http://www.sphinx-doc.org), to [Antora](./docs/what-is-antora.md). Fundamentally, not that much has changed. All of the same information is still available. However, here's what has changed:

1. The platform (and tools) used to build the documentation, which is [Antora](./docs/what-is-antora.md).
2. The file format that the documentation is written in, which is [AsciiDoc](./docs/what-is-asciidoc.md).
3. The <abbr title="User Interface">UI</abbr> & <abbr title="User Experience">UX</abbr> of the documentation

## Contributing to the Documentation

To get started contributing to the documentation, please refer to the [Getting Started Guide](./docs/getting-started.md).

## Generating the Documentation

To generate the documentation, whether in HTML or PDF format, please refer to the [Building the Documentation guide](./docs/build-the-docs.md).

## Common Content and Styling the Documentation

If you want to suggest an improvement to the ownCloud documentation theme, such as the layout, the header or the footer text, or if you find a bug, all the information that you need is in the `docs-ui` repository. Changes made in `docs-ui` are valid for the whole documentation.

Please read how to test un-merged [docs-ui](./docs/test-ui-bundle.md) changes with content from the ownCloud documentation.

## Best Practices and Tips

Please refer to [Best Practices and Tips for writing in AsciiDoc](./docs/best-practices.md) for more information.

## Target Branch and Backporting

Please always do your changes in `master` and backport them to the relevant branches.
The **ONLY** reason for doing a PR in a branch directly is, to fix an issue which is
_only_ present in that particular branch! When creating a PR and it is necessary to backport,
document in the PR to which branches a backport is needed.

When backporting, consider using the [backport script](https://doc.owncloud.com/server/developer_manual/general/backporting.html)
which eases life a lot and speeds up the process. It is also very benificial when using the
extended code provided, that a clear naming structure of the backport PR is generated automatically.

## Version branches in this repo

When doing a `10.x` release of ownCloud Server a version branch should be created from `master` by doing the following steps:

1. Create new `10.x` branch based on `origin/master`
2. Set `latest_version` in `.drone.star` to `10.x`
3. Adjust `asciidoc.attributes` in `site.yml` (increment `-version` values usually)
4. Commit changes to `10.x` branch
5. Create `add-10.x` branch based on `10.x` branch
6. Add `10.x` branch to `content.sources` in `site.yml` where the url points to this repo on `add-10.x` branch
7. Push `add-10.x` branch
8. Set `version` in `antora.yml` on `10.x` branch
9. Push `10.x` branch
10. Send PR `add-10.x` -> `master`
