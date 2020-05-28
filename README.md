# tron-operator-toolchain-template# tron-operator-ci_cd

## To get started, click this button:
[![Create toolchain](https://cloud.ibm.com/devops/graphics/create_toolchain_button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fjauninb%2Ftron-operator-toolchain-template&env_id=ibm:yp:us-south&source_provider=githubconsolidated)

## Final steps - Post-creation update

### Generic Webhook creation

1) Create a generic webhook to trigger the deployment and test part of the process
   - Keep the default _Token Matches_ validation
   - Select `ansible-operator-cd-webhook` as the Event Listener
   - Set the **Token source** to `Header`.
   - Set the **Header Key Name** to `X-ci-cd-operator-token`.

2) Update the Environment Properties:
   - Copy the Webhook URL to the Environment Property **env_prop-cd-trigger-webhook**
   - Copy the Secret to the Secured Environment Property **ci-cd-operator-token**.

3) Save the Tekton Definition

### (Optional) Ansible Roles/Collections installation

You may need to add your github.ibm.com SSH key to be able to perform Ansible Galaxy install of collections/roles.

You need to set values for the Secured properties: `github-ibm-com-id_rsa-pub` and `github-ibm-com-id_rsa-base64`.
If you SSH key are defined in `tron_id_rsa.pub` and `tron_id_rsa files`, then:
- For `github-ibm-com-id_rsa-pub`, perform
  ```
  clip < tron_id_rsa.pub
  ```
  and paste the value in `github-ibm-com-id_rsa-pub` environment property

- For `github-ibm-com-id_rsa-base64`, perform
  ```
  base64 tron_id_rsa -w0 | clip
  ```
  and paste the value in `github-ibm-com-id_rsa-base64` environment property

