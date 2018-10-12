
# Introduction
In Lab 1 you created and deployed an app to IBM Cloud, in Lab 2, you have created your model with Watson Studio.
In Lab 3 you will call your model form your web app.



# Objective
In the following lab, you will learn:

+ How to call your model form a Node.js application
+ How to get the scoring data
+ Feel free to improve your app


# Pre-Requisites
You successfully completed Lab 1 et Lab 2


# Steps

1. [Configuration](#step-1---configuration)
2. [Get your scoring data](#step-2---get-your-scoring-data)
3. [Push your app to IBM Cloud](#step-3---push-your-app-to-IBM-Cloud)
4. [Improvements](#step-4---Improvements)



# Step 1 - Configuration

1. On your local environement, open the file "app.js" with a code editor, you need to configure few things to be able to call your machine learning model
 
 You need to edit it to complete the following informations:
 ```
var wml_service_credentials_url ='<url>'; // TO COMPLETE
var wml_service_credentials_username = '<username>'; // TO COMPLETE
var wml_service_credentials_password = '<password>'; // TO COMPLETE

 ```

 2. Line 115 you also need to fill the scoring_url with the information you got from Watson Studio (Node.js code snippet):

 ```
// TO COMPLETE
const scoring_url = "https://us-south.ml.cloud.ibm.com/v3/wml_instances/<yourinstance>/deployments/<yourdeployment>/online";
 ```


# Step 2 - Get your scoring data

Your are now able to get your scoring data.
The table of 10 clients in your web app represent test clients, with who you can test your machine learning model.

1. Run your application locally with your Node.js server, from your application repository:

  ```
  $ npm start
  ```
 Watch carrefully your server logs and your clients logs (from your browser developer tools), they must give you information about what kind of data the scoring gives to you.

2. Edit the file public/page1.html with a code editor and at the end of the file in the 'script' section:

<img src="./images/code.png.png" width="80%"/>

3. This function is called whe you click the "Will Churn ?" button. So to get the logs, look for clients details from the home page, like for  client "2048"  for example. Then scroll down the page and click on the "will churn ?" button. Look at the logs.

4. From the function "displayChurn()" in page1.html, parse the "data", in order to extract the confidence value of a "YES the client will churn".

5. You need to display the result between 0 and 100 %. The result is in the "value" part of the scoring result. It's in the last array of the values and the "true" corresponding confidence rate is the second element.
For example, here, the result is "False", because the client will churn with a confidence of 0,23....

<img src="./images/example.png.png" width="80%"/>

You will give the "True" confidence only, with 2 numbers after the coma.


# Step 3 - Push your app to IBM Cloud

When your result is locally satisfying, test it with several clients of the database.

Then push back your app to IBM Cloud:

  ```
  $ ibmcloud cf push
  ```

# Step 4 - Improvements

your app is now finishe and online, but if you still have some time, here are the improvements you can add to your app:

- add a Gauge instead of the big number for the scoring result to improve the visualization

- add a big "YES" or " No" depending of the value of the scoring

- Impress us with your UI improvement and push your app to IBM cloud when you're done !
