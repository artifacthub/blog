---
title: "Artifact Hub CLI tool (ah)"
date: 2021-08-26T00:00:00-05:00
author: "Matt Farina"
authorLink: "https://mattfarina.com"
slug: "ah-cli"
---

Artifact Hub leverages metadata stored in annotations. This metadata provides details such as the images in use, if something is an operator, and more. Annotations provide an easy way to convey this information. Wouldn't it be great to check these annotations before cutting a release? Now you can with the `ah` command line tool.<!--more-->

## Getting ah

There are two ways you can use the `ah` tool. First, you can install the binary. You can [get the binary from the releases page on GitHub or install it on Mac via Homebrew or on Windows via Scoop](https://artifacthub.io/docs/topics/cli/#install).

The second way you can get `ah` is by using [the container image](https://artifacthub.io/docs/topics/cli/#docker). This container image can be used in testing tools and other automation to help catch any issues.

## Using ah

The `ah` tool is pretty straight forward to use. Aside from the `help` and `version` commands, the primary command is `lint`. The following example is `ah` run against the Artifact Hub chart.

```console
$ ah lint -p artifact-hub

------------------------------------------------------------------------------------------------------------------------
✓ artifact-hub 1.1.1 (artifact-hub)
------------------------------------------------------------------------------------------------------------------------

Package lint SUCCEEDED!

✓ Name: artifact-hub
✓ Version: 1.1.1
✓ App version: 1.1.1
✓ Description: Artifact Hub is a web-based application that enables finding, installing, and publishing Kubernetes packages.
✓ License: Apache-2.0
✓ Logo URL: https://artifacthub.github.io/helm-charts/logo.png
✓ Home URL: https://artifacthub.io
✓ Deprecated: false
✓ Pre-release: false
✓ Contains security updates: false
✓ Readme: PROVIDED
✓ Keywords:
  - kubernetes
  - helm
  - falco
  - opa
  - olm
  - tinkerbell actions
  - krew
  - tekton
  - keda scalers
  - coredns
  - keptn
! Links: *** NOT PROVIDED ***
✓ Maintainers:
  - Name: Sergio | Email: tegioz@icloud.com
  - Name: Cintia | Email: cynthiasg@icloud.com
  - Name: Matt | Email: matt@mattfarina.com
✓ Containers images:
  - Name: db-migrator | Image: artifacthub/db-migrator:v1.1.1
  - Name: hub | Image: artifacthub/hub:v1.1.1
  - Name: tracker | Image: artifacthub/tracker:v1.1.1
  - Name: scanner | Image: artifacthub/scanner:v1.1.1
  - Name: trivy | Image: aquasec/trivy:0.19.2
✓ Changes:
  - Kind: changed | Description: Helm charts repository moved to a new location
    - Links:
      - Name: New location | URL: https://artifacthub.github.io/helm-charts/
  - Kind: fixed | Description: Tracker and scanner containers resources were not being set properly
  - Kind: fixed | Description: Regression in logger middleware
! Recommendations: *** NOT PROVIDED ***
✓ Operator: false
✓ Values schema: PROVIDED
! Sign key: *** NOT PROVIDED ***

------------------------------------------------------------------------------------------------------------------------

1 package(s) found, 0 package(s) with errors
```

This was a successful run. What would happen if a field Artifact Hub was expecting had malformed data? To illustrate this, I took the same chart and altered the annotations so the content was malformed. The output of running `ah` against it shows us where the problem is at:

```console
$ ah lint -p artifact-hub

------------------------------------------------------------------------------------------------------------------------
✗ artifact-hub 1.1.1 (artifact-hub)
------------------------------------------------------------------------------------------------------------------------

Package lint FAILED. 1 error(s) occurred:

  * invalid annotation: invalid images value

------------------------------------------------------------------------------------------------------------------------

1 package(s) found, 1 package(s) with errors

Error: lint failed
```

When there is an error, `ah` exits with a non-zero exit code.

## Supported Packages

Currently, `ah` only supports Helm charts. Support for more package types is coming soon. If you would like to help contribute to that effort or otherwise expand on the features of `ah`, [the source is up on GitHub](https://github.com/artifacthub/hub/tree/master/cmd/ah) and we are happy to accept contributions.

## Conclusion

Adding the `ah` tool to your CI testing and your development workflow is a great way to make sure you have the annotations right before publishing your package and seeing the information up on the Artifact Hub. It also provides an easy place to start contributing to Artifact Hub, if you need additional features or have idea.
