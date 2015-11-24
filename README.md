# Elephant Carpaccio - sample pricing engine in nodejs
## Introduction
Incremental development is an important habit of the Agile Mindset.

[Alistair Cockburn](https://en.wikipedia.org/wiki/Alistair_Cockburn) created the [Elephant Carpaccio Exercise](http://alistair.cockburn.us/Elephant+Carpaccio+Exercise) to help coders and product owners get into the mood.

## The Situation
To enter the exercise imaging the following context.

A small startup is in the business of selling meat online. So far, they purchased a web application allowing customers to select a product and a quantity to purchase, **The Store**.

The founders' business plan foresees to roll out the application to several states in the US. All they need is a service able to calculate taxes depending on the state of delivery, **The Pricing Engine**. They will hire a contractor to deliver that service.

This is where the exercise begins, participating teams play the role of those contractors. The startup is short on budget, you better help them earn money quickly ...

We are aiming for a _Self-funding project_. Slicing the problem in thin vertical slices to laminate the solution is the approach agile organizations take, it allows for [Design by Knowledge Acquisition](http://alistair.cockburn.us/Design+as+Knowledge+Acquisition) and [Disciplined Learning](http://alistair.cockburn.us/Disciplined+Learning).

## The Pricing Engine
- This repository implements an empty pricing engine.
- It provides a starting point for the exercise.
- It displays the engine specification and a simple user interface to submit values to the engine

## Deploying the pricing engine on Bluemix
In this section, you will create your Bluemix account, deploy an empty pricing engine written in nodejs, use Bluemix DevOps web editor to modify the engine implementation and deploy your changes and finally connect your pricing engine to the main store.
- Go to [ibm.com/bluemix](http://ibm.com/bluemix) and click Sign Up

  ![Go to ibm.com/bluemix](instructions/01-go-to-bluemix.png)

- Fill out and submit your information

  ![Register](instructions/02-register.png)

  ![Register](instructions/03-registering.png)

  ![Register](instructions/04-check-your-emails.png)

- Wait for the activation link in your emails

  ![Register](instructions/05-activate.png)

- Go to [ibm.com/bluemix](http://ibm.com/bluemix) and Log in

  ![Register](instructions/06-login.png)

  Once logged, the Bluemix console is shown on the dashboard:  

  ![Register](instructions/07-logged.png)

- Push the deploy button below:

  <a href="https://bluemix.net/deploy?repository=https://github.com/l2fprod/carpaccio-pricing" target="_blank">![](https://bluemix.net/deploy/button.png)</a>

- Click "Log In" to connect to Bluemix DevOps

  ![Register](instructions/10-login-to-deploy.png)

- If you never connected to Bluemix DevOps before, you will be prompted to define an alias to be used by DevOps services

  ![Register](instructions/11-pick-devops-alias.png)

  ![Register](instructions/12-continue.png)

- From here you will be taken to a page, where you will be prompted to name your pricing engine. A sample name is provided for you, but feel free to give your application any name you like (if the name is taken by another user, you will be prompted to try another name).

  **Note:** You can keep the default settings for Region, Organization and Space.

  ![Register](instructions/13-select-region-org-space.png)

- Once you have named your application, click the Deploy button to begin the deploy process to IBM Bluemix. During this process, IBM Bluemix will automatically build and deploy our application based on the GitHub repository.

  ![Register](instructions/14-and-deploy.png)

- Once the application has finished deploying, you will see a **Success!** message.

  ![Register](instructions/15-congrats.png)

  The process has created a new private DevOps Services project, a git clone of the lab source code repository, built your application and deployed it to IBM Bluemix. In addition, it configured a Build & Deploy pipeline that will get triggered whenever your commit changes to the Git repository.

- Click **View Your App** to access the deployed application

  ![Register](instructions/16-view-app.png)

- We are now going to perform changes to the running application. Back to the "Deploy to Bluemix" page, click **Edit Code**

  ![Register](instructions/17-edit-app.png)

- This opens the Web Editor on your app

  ![Register](instructions/18-web-editor.png)

  The web editor allows to modify and commit changes to the project without leaving your web browser.

  It comes with a **Live Edit** feature allowing to modify the changes to the running app without having to commit the changes to the code to the Git repository. We will enable and use this feature in the next steps to accelerate the round trip between changing the code and viewing the impact of the change on the deployed app.

- Enable **Live Edit** by clicking on the switch

  ![Register](instructions/19-enable-live-edit.png)

- Click **OK** when prompted

  ![Register](instructions/20-live-edit-ok.png)

- Wait until **Live Edit** is enabled for the app. Notice the indicator near the project name shows the status of enabling Live Edit for your app

  ![Register](instructions/21-enabling-live-edit.png)

- After a short while, the project indicator becomes green again. **Live Edit** is enabled.

  ![Register](instructions/22-live-edit-enabled.png)

- Open the file **app.js** which contains the pricing engine implementation

  ![Register](instructions/23-open-backend.png)

- Line 23 shows the implementation of the /pricing endpoint. Currently it returns a 501 error code (Not Implemented)

  ![Register](instructions/24-modify-backend-with-error.png)

- To illustrate the **Live Edit** feature, let's modify the implementation. Instead of simply returning the error code, we will also add a message.

  The new code reads as:

  ```
  res.status(501).send({error: "this is not implemented"})
  ```

  Once modified, click the "Restart the App Without Redeploying" button

  ![Register](instructions/25-push-modifications-on-the-fly.png)

- Let's do another change, this time we show a dummy implementation return 0 as the totalPrice for the transaction

  ```
  res.send({totalPrice: 0})
  ```

  ![Register](instructions/26-another-modification-sending-a-price.png)

  Once modified, click the "Restart the App Without Redeploying" button

- Testing the change

  ![Register](instructions/27-it-works!.png)

  At this point you are equipped to perform quick changes to your app and to have them taken into account by the store.

- To register your pricing engine with the store, on the store homepage, click **Register a pricing engine**

  ![Register](instructions/34-register-pricing.png)

- Enter your engine information and click **Register**

  ![Register](instructions/35-add-endpoint.png)

  ![Register](instructions/36-added.png)

### Committing changes to the main repository
Up to this point, all the changes you made are local to the web editor and have not been committed to the Git repository for your project.
- To commit the changes made in the web editor, switch to the Git view

  ![Register](instructions/28-git-view.png)

- Select the changes to commit

  ![Register](instructions/29-commit-select-all.png)

- Type a message and click Commit

  ![Register](instructions/30-commit-message.png)

- To push the changes from the web editor Git repository to the master Git repository, use the Sync button

  ![Register](instructions/31-committed.png)

  ![Register](instructions/32-push-to-remote.png)  

  ![Register](instructions/33-done.png)

## Running the pricing engine on Bluemix
Use this section if you want to use your local development environment to develop and deploy your application.
- Create a Bluemix Account

   [Sign up][bluemix_signup_url] for Bluemix, or use an existing account.

- Download and install the [Cloud-foundry CLI][cloud_foundry_url] tool
- Clone the app to your local environment from your terminal using the following command

  ```
  git clone https://github.com/l2fprod/carpaccio-pricing.git
  ```

- cd into this newly created directory
- Edit the `manifest.yml` file and change the `<application-name>` and `<application-host>` from `carpaccio-pricing` to something unique.

  ```
   applications:
   - name: carpaccio-pricing
     host: carpaccio-pricing
     memory: 256M
  ```

  The host you use will determinate your application url initially, e.g. `<application-host>.mybluemix.net`.

- Connect to Bluemix in the command line tool and follow the prompts to log in.

  ```
   $ cf api https://api.ng.bluemix.net
   $ cf login
  ```

- Push the application to Bluemix.

  ```
  $ cf push
  ```

And voila! You now have your very own instance running on Bluemix. Navigate to the application url, e.g. `<application-host>.mybluemix.net`.

### Troubleshooting
To troubleshoot your Bluemix app the main useful source of information is the logs. To see them, run:

```sh
  $ cf logs <application-name> --recent
```

--------------------------------------------------------------------------------

This sample application is created for the purpose of supporting the exercise. The program is provided as-is with no warranties of any kind, express or implied.

[bluemix_signup_url]: https://console.ng.bluemix.net/?cm_mmc=GitHubReadMe-_-BluemixSampleApp-_-Node-_-Workflow
[cloud_foundry_url]: https://github.com/cloudfoundry/cli
