# backstage-orchestrator-workflows
Example serverless workflows for testing and demonstration of the [Orchestrator Backstage plugin](https://github.com/redhat-developer/rhdh-plugins/tree/main/workspaces/orchestrator)

## Notifications workflow
See [Sources](./workflows/send-notification.sw.yaml)

The `sendnotification` workflow demonstrates sending notifications via [Backstage's Notifications API endpoint](https://backstage.io/docs/notifications/).

### Prerequisites
- Backstage with the [Notifications](https://backstage.io/docs/notifications) plugin deployed
- use [shared-secret authentication](https://backstage.io/docs/auth/service-to-service-auth/#static-tokens) for external access of the Backstage backend API

  - hint for the `app-config.yaml`:
  ```yaml
  backend:
    baseUrl: http://localhost:7007
    auth:
      externalAccess:
        - type: static
          options:
            # echo mycurlpasswd | base64
            token: bXljdXJscGFzc3dkCg==
            subject: my-external-feed
  ```
- either configure [application.properties](./workflows/application.properties) or use set following environment variables when running the SonataFlow:
  - `BACKSTAGE_NOTIFICATIONS_URL`
  - `NOTIFICATIONS_BEARER_TOKEN`
