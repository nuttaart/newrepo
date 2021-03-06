---
title: "Add Authentication"
chapter: false
weight: 34
---

## Create Authentication Component

Next, you will add authentication capabilities for our application using Amazon Cognito. 

1. Run the following command to add an authentication component to this Amplify project
```bash
# Add authentication
amplify add auth
```
1. Select `Default configuration` for the first choice. 
![](/images/reactApp/auth_default_configuration.png)
1. Select `Email` when asked **How do you want users to be able to sign in?**. Use the arrow button on your keyboard to move up and down to select choice
![](/images/reactApp/auth_signin.png)
1. For **Do you want to configure advanced settings?**, choose `No, I am done`
1. You can use `amplify status` to show the execution plan
![](/images/reactApp/auth_amplify_status.png)

## Push changes to AWS

The **amplify add auth** command only saved files locally. We need to run the **amplify push** command to deploy our changes to our AWS account.

1. To push our changes to AWS, run the following
```bash
# push changes to AWS
amplify push
```
1. When prompted to complete the changes. Enter `Y` and the deployment will begin
1. You will see the updating progress, wait for this progress finished. This will take a few minutes.


## Update Authentication to web APP

To add the authentication component to React application, we make the following changes:

* Add the following code in **src/App.js** after all *import* statement
{{< highlight javascript >}}
import Amplify from 'aws-amplify'
import Aws_exports from './aws-exports.js'
import { withAuthenticator } from 'aws-amplify-react'

Amplify.configure(Aws_exports)
{{< /highlight >}}
  ![](/images/reactApp/amplify_imports.png?width=40pc)

* Wrap the web application with build-in **Authenticator**. Replace the origin export with the following code.
{{< highlight javascript >}}
export default withAuthenticator(withRouter(App));
{{< /highlight >}}
  ![](/images/reactApp/amplify_auth_wrapper.png?width=40pc)

## Test The Application

Now you can return to the preview tab for your application and verify that you can sign up and login to your application.

1. Go to the root URL of your application
1. A default Sign In web page will be displayed
1. Create **Create account**
![](/images/reactApp/auth_create_account.png?width=20pc)
1. Input the details. DO input **EMAIL** in the **username** field, we will use email as the username
![](/images/reactApp/auth_signup.png?width=20pc)
1. You will receive an activation code in your email, find the code and input on the confirmation page
![](/images/reactApp/auth_confirm.png?width=20pc)

{{% notice note %}}
We choose to use Email for the username when add authentication feature, so do input your email address in the **userename** field.
{{% /notice %}}

At this point, authentication is in place and working in our React app. Now, on to some more features??? adding the Sumerian AR.