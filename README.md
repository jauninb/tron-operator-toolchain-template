# tron-operator-toolchain-template# tron-operator-ci_cd

## To get started, click this button:
[![Create toolchain](https://cloud.ibm.com/devops/graphics/create_toolchain_button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fjauninb%2Ftron-operator-toolchain-template&env_id=ibm:yp:us-south&source_provider=githubconsolidated)

## Final steps - Post-creation update

### Generic Webhook creation

1) Create a generic webhook to trigger the deployment and test part of the process
   - Select `ansible-operator-test-webhook` as the Event Listener
   - Set the **Token source** to `Header`.
   - Set the **Header Key Name** to `X-tron-ci_cd-token`.
   - Add the trigger properties to the webhok:
     - `ansible-operator-configs-repository` with the same value as in the **test-operator-manual** trigger.
     - `ansible-operator-configs-branch` with the same values as in the **test-operator-manual** trigger.

2) Update the Environment Properties:
   - Copy the Webhook URL to the Environment Property **tron-cd-token**
   - Copy the Secret to the Environment Property **tron-cd-token**.

3) Save the Tekton Definition
