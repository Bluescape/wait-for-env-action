# bluescape/wait-for-env-action

## Description
This GitHub Action plugin will poll the health endpoint of a Bluescape Environment the environment is ready, or the timeout is hit.

## Usage
### Pre-requisites
Create a workflow `.yml` file in your `.github/workflows` directory. An example workflow is available below. For more information, reference the GitHub Help Documentation for [Creating a workflow file](https://help.github.com/en/articles/configuring-a-workflow#creating-a-workflow-file).

### Inputs
- `environment` (optional): The domain of the environment to wait on.
- `timeout` (optional): The amount of time (in minutes) to wait for the environment to be healthy.

## Example Workflow
Wait for a standard environment to be ready.
```yaml
  - name: Wait For Environment to be healthy
    uses: bluescape/wait-for-env-action@v1.0.1
    with:
      environment: apps.us.bluescape.com
      timeout: 10
```
Wait for a netlify environment to be healthy.
```
- name: Wait for Netlify client to be ready
  uses: bluescape/wait-for-env-action@v1.0.1
  with:
    environment: apps.us.bluescape.com
    is-netlify: true
    netlify-service: 'netlify'
    netlify-suffix: pr-${{ github.event.number }}
    output-variable: BLUESCAPE_URL
    timeout: 60
```
