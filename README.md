# Looker Marketplace Test Automation Action

This Action streamlines the validation of Looker Marketplace projects submitted by third party developers of Custom Visualiztions, Blocks and other Looker custom projects by validating Looker specific files.

## Tools

1. Jest
2. Test Reporter - Will report test results in GitHub Actions 
3. GitHub Actions CI - Will run tests on PR or Push

## What will be Tested
1. Existence of key files
    - README.MD 
    - LICENSE
    - One *.dashboard.lookml file 
2. Valid Marketplace.json file
3. Constants exist and match in:
    - Manifest.lkml
    - Marketplace.json
4. Constants are unique in Marketplace.json
5. Constants Labels are unique in Marketplace.json
6. File extensions for model/views are `.lkml` and not `.lookml`

## Setup

1. Add the folder named `/.github/workflows` to the Looker Marketplace repo to be tested. This tells GitHub you have a workflow to run.

2. Upload the workflow config file [`marketplace_automation.yml`](marketplace_automation.yml) to the `/.github/workflows` folder of the target Looker Marketplace repo to be tested. The workflow yml will contain a reference to this action (please verify the latest version)

3. Commit and PR to the target Looker Marketplace repo.

4. On GitHub Actions tab, see the CI execution flow and results of tests.

## Compiling Action

### If you need to make changes to this action:
- After making changes to index.js file and/or any other asset (for example, tests)
- run
```
ncc build index.js -o dist --source-map --license licenses.txt
```
- If `ncc` returns an error, you may need to install `@vercel/ncc` globally by running this first:
```
npm install -g @vercel/ncc
```
