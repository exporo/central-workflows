
# Central-workflows
Reusable workflows for Exporo organization github actions

## CICD Usage example
**Configure Environment**
 - Create **Development**,  **Stage** and **Production** environment.
 - Create **AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY** secrects keys in each environment.
 -  On **Production** add  **Required reviewers**  to hold production deploys without approval

**Configure Repository**
-    create file - ./.github/worflows/CICD.yml

	  
	name: CI + CD
	on:
	  push:
	    branches: [main]
	  pull_request:
	    branches: [main]
	  workflow_dispatch:

	jobs:
	  CICD:
	    uses: exporo/central-workflows/.github/workflows/CICD.yml@main
	    secrets:
	      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
	      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
