# Steps to be followed for Project Development

![block-diagram](https://user-images.githubusercontent.com/64250870/81781272-7fd8fc00-9515-11ea-8752-276c244ad1ea.png)

* A IBM Cloud Account is to be created (can be under Academic Initiative optionally for added benefits).

>The IBM cloud platform combines platform as a service (PaaS) with infrastructure as a service (IaaS) to provide an integrated experience. 

# Create Watson discovery service: 

* An IBM Discovery Service is to be created following the given below steps

**Step 1 :** Select the Discovery services from Catalog >> Service >> AI. Click on [CREATE].

**Step 2 :** Once the service has been created, generate service credentials. Save API Key and URL credentials. It will be used later.

**Step 3 :** Launch the Watson Discovery tool.

>IBM Watson Discovery, allows ingestion, normalization, enrichment, and search of unstructured data (JSON, HTML, PDF, Word, and more) with >speed and accuracy. It packages core Watson APIs such as Natural Language Understanding and Document Conversion along with UI tools. 

**Step 4 :** Save the COLLECTION ID & ENVIRONMENT ID for the pre - enriched data Watson Discovery News provided. We will be querying this data using our Node - Red app           

>Watson Discovery News is an indexed dataset that is pre-enriched with the following cognitive insights: Keyword Extraction, Entity >Extraction, Semantic Role Extraction, Sentiment Analysis, Relation Extraction, and Category Classification.

# Build Node - Red User Interface: 
* A Node-RED Application is to be created following the given below steps 

**Step 1 :** Select the Node-Red App starter kit from Catalog >> Software.Click on [CREATE APP].

**Step 2 :** Configure in the App details. Choose a Cloudant Databse service region. Click on [CREATE]. Thus, the application and the resources it requires have been created.

**Step 3 :** Enable the Continuous Delivery feature to deploy the application into the Cloud Foundry space of IBM Cloud. Create an IBM Cloud API Key to allow the deployment process to access the resources.
Select the region of of deployement as the one in which the Cloudant instance had been created. Finally, select the region for DevOps    Toolchain. Click on [CREATE].

**Step 4 :** From Resource List >> Node - Red App. Click [Visit App URL] link to access Node-RED Starter application.  

>Node-RED is built on Node.js, taking full advantage of its event-driven, non-blocking model. This makes it ideal to run at the edge of >the network on low-cost hardware such as the Raspberry Pi as well as in the cloud.

**Step 5 :** To add the node-red-dashboard module to Node-Red palette, go to your git repository from the continuous delivery box. Add “node-red-dashboard” : “2.x”,on top of dependencies in the package.json. Click [COMMIT CHANGES].

**Step 6 :** Create the given Node-Red flow along with the necessary changes to be done in each node as provided below.

![node-red-flow](https://user-images.githubusercontent.com/64250870/81781274-80719280-9515-11ea-8ea6-ff68e93da303.png)

![function1-node-prop](https://user-images.githubusercontent.com/64250870/81781280-81a2bf80-9515-11ea-9c17-6eaf727236d3.png)

![form-node-prop](https://user-images.githubusercontent.com/64250870/81781276-810a2900-9515-11ea-9478-153e5abf99d9.png)

![discovery-node-prop](https://user-images.githubusercontent.com/64250870/81781277-810a2900-9515-11ea-9252-32730ebf6435.png)

![function2-node-prop](https://user-images.githubusercontent.com/64250870/81781266-7e0f3880-9515-11ea-8a22-6d79788cb79f.png)

![text-node-prop](https://user-images.githubusercontent.com/64250870/81781269-7f406580-9515-11ea-9163-086865189356.png)

![function3-node-prop](https://user-images.githubusercontent.com/64250870/81781270-7fd8fc00-9515-11ea-83cf-2184ec339a24.png)

![chart-node-prop](https://user-images.githubusercontent.com/64250870/81781321-90897200-9515-11ea-8989-dede456e0422.png)

**Step 7 :** Deploy the app. Go to the website link associated with the particular Node-Red App. Query topics related to which, news article will be provided along with the sentiment they represent.

![deployed-website](https://user-images.githubusercontent.com/64250870/81781324-91220880-9515-11ea-9e2b-952722b2e0d6.png)

# Deploying Discovery news app and integrating with slack-bot:
 
* NOTE : The app is locally run due to instantaneous cloud runtime memory constraints. 

**Step 1 :** Use the following command to clone the watson-discovery-news GitHub repository.
        <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*git clone https://github.com/ibm/watson-discovery-news*
        
**Step 2 :** From the home directory of your cloned local repo, create a .env file by copying it from the sample version.
        <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*cp env.sample .env*
        
**Step 3 :** Copy and paste the apikey and URL values from your Watson Discovery service credentials into the .env file.

**Step 4 :** Go to *https://<myspace.slack.com>/apps/manage/custom-integrations*, where *<myspace.slack.com>* is the Slack workspace to be customized

**Step 5 :** From the Cutsom Integrations page, select the Bots option. 

![bot-integration](https://user-images.githubusercontent.com/64250870/81781311-8ebfae80-9515-11ea-9092-c5cfbd03d43b.png)

**Step 6 :** To add a new bot, select the [Add Configuration button]. Enter a username for the bot and click [Add bot integration]. Once created, save the API Token that is generated. 

**Step 7 :** Edit the .env file and enter the Slack Bot API Token saved.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
*SLACK_BOT_TOKEN=<slack_bot_token>*

**Step 8 :** Finally, run the application. Use the below commands.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*npm install*<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
*npm start*
 
The application will be available at http://localhost:3000. Also now you can access the bot from slack after adding it to a channel.

