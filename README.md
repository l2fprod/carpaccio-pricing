# Elephant Carpaccio - sample pricing engine in nodejs

Introduce the game

## The pricing engine

* This repository implements an empty pricing engine.
* It provides a starting point for the exercise.
* It displays the engine specification and a simple user interface to submit values to the engine

## Deploying the pricing engine on Bluemix

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/l2fprod/carpaccio-pricing)

Using this button, you can get your own pricing engine deployed to Bluemix very quickly. It will also create a Bluemix DevOps project so that you can modify code using your web browser and have it automatically redeployed. If you'd like to get your own copy of the code locally and deploy from your machine, follow the next steps.

## Running the pricing engine on Bluemix

1. Create a Bluemix Account

    [Sign up][bluemix_signup_url] for Bluemix, or use an existing account.
    
2. Download and install the [Cloud-foundry CLI][cloud_foundry_url] tool

3. Clone the app to your local environment from your terminal using the following command

  ```
  git clone https://github.com/l2fprod/carpaccio-pricing.git
  ```
  
4. cd into this newly created directory

5. Edit the `manifest.yml` file and change the `<application-name>` and `<application-host>` from `carpaccio-pricing` to something unique.

	```
    applications:
    - name: carpaccio-pricing
      host: carpaccio-pricing
      memory: 256M
	```

  The host you use will determinate your application url initially, e.g. `<application-host>.mybluemix.net`.

6. Connect to Bluemix in the command line tool and follow the prompts to log in.

	```
	$ cf api https://api.ng.bluemix.net
	$ cf login
	```

7. Push the application to Bluemix.

  ```
  $ cf push
  ```

And voila! You now have your very own instance running on Bluemix. Navigate to the application url, e.g. `<application-host>.mybluemix.net`.

### Troubleshooting

To troubleshoot your Bluemix app the main useful source of information is the logs. To see them, run:

  ```sh
  $ cf logs <application-name> --recent
  ```
  
---

This sample application is created for the purpose of supporting the exercise. The program is provided as-is with no warranties of any kind, express or implied.

[bluemix_signup_url]: https://console.ng.bluemix.net/?cm_mmc=GitHubReadMe-_-BluemixSampleApp-_-Node-_-Workflow
[cloud_foundry_url]: https://github.com/cloudfoundry/cli
