---
changelog: 
last_modified_at: 
title: Sensitive input in public apps
redirect_from:
- "/sensitive-input-field/"
tag:
- public
- env vars
- builds
- secrets
description: Hide sensitive inputs with secret Environment Variables  in your public
  apps, so that those inputs cannot be viewed in build logs or the `bitrise.yml` of
  your build.
menu:
  builds-main:
    weight: 19

---
Any sensitive information such as passwords, IDs, and API tokens are exposed in the build logs/bitrise.yml of your public apps, hence visible to anyone who has the build URL of the app. You can hide these inputs with secret Environment Variables (Env Vars) so that those are not available in build logs/`bitrise.yml`. To make the sensitive input fields obvious in our Workflow Editor, we've marked them with a yellow **SENSITIVE** label in Steps holding sensitive input fields. These inputs must be defined with the help of secret Env Vars and not with Env Vars!

You can hide any input of your choice with secret Env Vars even if the field is not labeled **SENSITIVE** but you must use secret Env Vars for fields which are by default marked as **SENSITIVE**.

![Screenshot](/img/builds/sensitive-label.png)

There are two ways to define secret Env Vars:

* Directly [in the steps](/sensitive-input-field/#set-a-sensitive-input-in-a-step/).
* In the [Secrets tab](/builds/env-vars-secret-env-vars#about-secrets) of your Workflow Editor and select the secret Env Var in a step input when needed.

Head over to [Secrets and Env Vars](/builds/env-vars-secret-env-vars/) to find out the difference between Env Vars and Secrets!

## Set a sensitive input in a step

1. Click the **Select Secret Variable** button below the input field which is marked with the yellow **SENSITIVE** label.
2. In the **Insert variable** pop-up, browse the **Choose Secret Env Var** list or create a new secret env var (add the key and the value) in the **Create New Secret Env Var** section.

   ![](/img/insert-variable-1.png)

   The **Expose for pull request?** toggle under the **Value** field is by default disabled and cannot be enabled with public apps to protect the secrets of your public app in the case of pull requests.
3. If you've entered a new Env Var, hit **Add new**.

The new secret Env Var will be available in the **Choose Secret Env Var** list or under the **Secrets** tab for your app for future reference/use.

The selected or newly created secret env var will get automatically saved into the input field of the step.

![](/img/select-secret-variable.png)

You can always modify the secret Env Var registered for a **SENSITIVE** input field if you click the **Select secret variable** button or head over to the **Secrets** tab where you get a full list of your secret env vars.

{% include message_box.html type="important" title="Select secret variable" content=" Note that you cannot modify the input manually in the input field marked with the **SENSITIVE** label! Instead, click the **Select secret variable** to replace the existing input with another secret Env Var from the list or to create a new one in the **Insert variable** pop-up. "%}

* Do NOT ADD PRIVATE INFORMATION in the **Env Var** tab! Our **Secrets** tab is designed to hold encrypted inputs as secret Env Vars which will not be exposed in `bitrise.yml` or in public app PRs.
* Note that secret Env Vars can only hide sensitive information in the build logs of your public app. If you attach any other file to your build log which contains sensitive information but it is not encrypted, then sensitive information will be visible to anyone who has the build URL!

{% include banner.html banner_text="Set a sensitive input in a Step" url="https://app.bitrise.io/dashboard/builds" button_text="Go to your app" %}