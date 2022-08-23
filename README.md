# GitHub Data Workflows

This repo contained the GitHub actions and reusable workflow used for the CICD of data platform project.

## Standard Project Workflows

A Standard Data Plat project, as 2 environment: dev and live.
There will usually be 3 workflows:
- `main-pr.yaml`: validation steps
- `main-push.yaml`: apply changes in dev
- `release.yaml`: apply changes in live

Please check our template project [here](https://github.com/Ki-Insurance/data-plat-template/tree/main/.github/workflows), for examples.


## Use GitHub Action separately

You can also decide to use the GitHub Actions without the workflow, for example:
```yaml
  flux-check-live:
    runs-on: ubuntu-20.04
    name: Flux Check LIVE
    steps:
      - name: checkout
        uses: actions/checkout@v2.4.0
      - name: check flux deployment status
        uses: Ki-Insurance/github-data-workflows/.github/actions/kubernetes/check-flux-deployment@v1
        with:
          environment: live
          gcp-service-account-key: xxxx
          cluster-name: xxxxx
          cluster-project: xxxxx
```
