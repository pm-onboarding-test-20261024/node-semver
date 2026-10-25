# PackageMaze production verification

This independent fork verifies npm installation and publication through the
`pm-onboarding-test-20261024/npm` Feed.

The manual workflow is `.github/workflows/packagemaze.yml` on `main`. Its install
and publish permissions are separate. Publication is limited to
`@pm-onboarding-test-20261024/semver`.

[Run 40135597721](https://github.com/pm-onboarding-test-20261024/node-semver/actions/runs/40135597721)
passed on 24 October 2026 at commit `80bebf621f068a1f9c53cac4ed0d4c6848f6a820`.
It installed dependencies, ran the upstream tests in a separate job without
package credentials, published the built tarball, and installed the exact
published version. The downloaded tarball matched the original bytes.

| Result | Value |
| --- | --- |
| Published version | `7.8.5-verify.40135597721.1` |
| Tarball size | 29,492 bytes |
| Tarball SHA-256 | `2947326444e016573e1376b375ad46be2e3bedaa4200e100584d722b587fbdc6` |

The npm CLI produced a Sigstore provenance bundle, which PackageMaze retained.
That records the publication evidence; the separate PackageMaze Trust
evaluation was not performed by this workflow.

The workflow runs only when manually dispatched. Updating this record does
not publish another package version.
