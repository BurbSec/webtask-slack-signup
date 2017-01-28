By: @J0hnnyXm4s

Create Slack signup page using Auth0 webtasks to generate a js file which will cause a full signup page to be rendered in a user's browser without requiring hosting.

Follow these 3 steps to install the webtasks.io cli and create a webtask URL to pass around:

```bash
npm install -g wt-cli
wt init
wt create https://raw.githubusercontent.com/BurbSec/webtask-slack-signup/master/slack-invite.js \
    --name {your_slack_team}-signup \
    --capture \
    --secret SLACK_ORG={your_slack_team} \
    --secret SLACK_TOKEN={your_slack_admin_token} \
    --secret BG_URL={url_for_header_image} \ 
    --secret LOGO_URL={url_for_logo_image} \
    --parse-body
```

The `{your_slack_admin_token}` can be obtained from Slack [here](https://api.slack.com/docs/oauth-test-tokens). Currently this only works with TEST tokens; unsure why. Possibly either because prod tokens require an associated Client_ID to be passed, or a registered redirect URL (see above likn for info). Feel free to figure it out!

You can add any other variables you want to the js file, and just pass values to them using --secret, as above.
