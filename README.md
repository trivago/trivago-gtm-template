# trivago GTM Template

trivago GTM template implementation for Conversion API connection.

## Getting Started

These instructions will help you integrate trivago template as a new tag for GTM.

### Prerequisites

Before installing the tag make sure that you have:

* installed GTM for your website and learnt about terms like "tag" and "trigger". More on that topic [here](https://tagmanager.google.com/#/home)
* received the advertiser ID and all the neccessary information from trivago beforehand
* confirmed the usage of GTM Tag with trivago for whitelisting

### Installing

#### Set up new variables

Note the existing variables or create a new variables for required tag parameters.

1. Define the variables that are going to be passed to the tag and shared with trivago.
2. -N Set up the variable data for each one.

We'll go through the set up of the trv_reference variable as it requires some manual code.

##### Set up the trv_reference

The trivago reference or click id is appended to the booking link after the clicking out of the trivago platform. For example:
```
https://example.com/?param1=123&trv_reference=ref_1
```
The recommended way would be to extract this value and store it as a 1st party cookie for 30 days. For this we can do the following:

1. Create new variable by navigating to **Variables** menu;
2. Click **New** under the **User-Defined Variables** section;
3. Click on **Variable configuration** card;
4. Select the variable type as a **1st-Party Cookie**;
5. Type under the **Cookie name** the value **GTM_TRV_REFERENCE_TR** or the other one but note it somewhere;
6. Type the variable name on the top of the page as **trv_ref**;
7. Save the variable and go to the **Tags** page;

Now let's create new tag that will detect the url containing the trv_reference parameter and store it as a cookie:

1. Click on **New** button to create new tag;
2. Click on the tag configuration and select tag type as **Custom HTML**;
3. Insert the following code:
```javascript
<script>
 
var cookieName  = "GTM_TRV_REFERENCE_TR"; 
var url = new URL("{{Page URL}}");
var cookieValue = url.searchParams.get("trv_reference");
var cookiePath  = "/";
var expirationTime = 2678400;                           //time the cookie should expire in seconds
expirationTime = expirationTime * 1000;                 //Convert expirationtime to milliseconds
 
var date = new Date();                                  //Create new date
var dateTimeNow = date.getTime();                       //What is the current time in milliseconds
date.setTime(dateTimeNow + expirationTime);             //Set expiration time
var expirationTime = date.toUTCString();                //Convert milliseconds to UTC time string
document.cookie = cookieName+"="+cookieValue+"; expires="+expirationTime+"; path="+cookiePath;  //Set cookie
</script>
```
Don't forget to update the cookieName if that was changed earlier;

Now let's configure the trigger for that tag:
1. Close the tag configuration and open the trigger selection window;
2. Click on **+** to create a new trigger and select the **Page view** type;
3. Select **Some Page Views** radio button;
4. Modify the settings and configure the trigger to fire only one **Page URL** containing **trv_reference**![Image of settings](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/settings.png)
5. Save the trigger and tag;
6. Publish new version of the container.

##### Set up the remaining variables

Other variables would require custom set up. If you already have variables in use for example like booking_id or arrival dates, you can reuse them. 
Let's go through the set up of the variable that take the value from the booking confirmation page. We'll use this page for this https://gaikanomer9.github.io/?trv_reference=c91fe358-e3c1-4c24-a427-bece84fe6658

We'll set up the **hotel** variable.

1. Create the new **User-Defined Variable** and select **DOM Element** as the type of that variable;
2. One the booking confirmation page select the id of the desired the element. (if you are using Chrome click on the element with right button and select **Inspect**![Image of settings](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/id.png)
3. Save the variable by the desired name and later use it in tag set up


#### Adding new trivago Tag to the workspace

1. From the GTM Workspace overview click on **Add a new tag**
2. Click on **Tag Configuration**
3. In the opened slide out "Choose tag type click on the **Discover more tag types in the Community Template Gallery**
4. Search or scroll for **trivago Conversion API** tag and click on it
5. Add the tag to the workspace by clicking **Add to workspace**
6. Check for the required permissions (in order for Conversion API to access the endpoint the usage of additional Javascript methods is needed and this requires the script injection permission from the trivago domain)
7. Return to the Tag selection page and select **trivago Conversion API**

#### Configuring the trivago Tag

1. Insert advertiser number and api key received by trivago
2. Configure the remaining fields through preconfigured variables

#### Configuring the trigger

1. Select the proper trigger for the event like visiting the booking confirmation page.

#### Publishing the changes

1. Click on the **Submit** button in the top-right location of the screen.

## Running the test

Inform trivago about implementing the GTM tag. After that we'll monitor the incoming bookings for some time and after matching the number of bookings from both sides the Conversion API could be considered implemented.
ss for submitting pull requests to us.
