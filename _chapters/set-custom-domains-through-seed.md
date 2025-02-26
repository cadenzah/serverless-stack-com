---
layout: post
title: Set Custom Domains Through Seed
date: 2018-03-15 00:00:00
lang: en
description: We will use the Seed console to configure our API Gateway endpoints in our Serverless project with custom domains. To configure a stage with a custom domain go to the stage settings, select the Route 53 domain, a sub-domain, and the base path.
context: true
ref: set-custom-domains-through-seed
comments_id: set-custom-domains-through-seed/178
---

Our serverless API uses API Gateway and it gives us some auto-generated endpoints. We would like to configure them to use a scheme like `api.my-domain.com` or something similar. This can take a few different steps through the AWS Console, but it is pretty straightforward to configure through [Seed](https://seed.run).

Head over to our app settings.

![Seed app pipeline screenshot](/assets/part2/seed-app-pipeline.png)

Here click on **Edit Custom Domains**.

![Click Edit Custom Domains in app settings screenshot](/assets/part2/click-edit-custom-domains-in-app-settings.png)

And click **Add** for our production endpoint.

![Click Add for production endpoint in custom domain settings](/assets/part2/click-add-for-production-endpoint-in-custom-domain-settings.png)

In the first part of the tutorial we had added our domain to Route 53. If you haven't done so you can [read more about it here](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html). Hit **Select a domain** and you should see a list of all your Route 53 domains. Select the one you intend to use. And fill in the sub-domain and base path. For example, you could use `api.my-domain.com/prod`; where `api` is the sub-domain and `prod` is the base path.

And hit **Add Custom Domain**.

![Click Add Custom Domain button for prod endpoint](/assets/part2/click-add-custom-domain-button-for-prod-endpoint.png)

Seed will now go through and configure the domain for this API Gateway endpoint, create the SSL certificate and attach it to the domain. This process can take up to 40 mins.

While we wait, we can do the same for our `dev` endpoint. Select the domain, sub-domain, and base path. In our case we'll use something like `api.my-domain.com/dev`.

![Click Add Custom Domain button for dev endpoint](/assets/part2/click-add-custom-domain-button-for-dev-endpoint.png)

Hit **Add Custom Domain** and wait for the changes to take place.

Once complete, we are ready to test our fully-configured serverless API backend!
