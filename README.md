# trivago GTM Template

trivago GTM template implementation for Conversion API connection.

## Support and questions

If you have questions about the installation process or not sure about anything feel free to get in touch via email: nikita.zavyalov@trivago.com

## Getting Started

These instructions will help you integrate trivago template as a new tag for GTM.

### Prerequisites

Before installing the tag make sure that you have:

* installed GTM for your website and learnt about terms like "tag" and "trigger". More on that topic [here](https://tagmanager.google.com/#/home)
* received the advertiser ID and all the neccessary information from trivago beforehand
* confirmed the usage of GTM Tag with trivago for whitelisting

### Installing

Installation consists of 3 steps:
* specifying the variables;
* installation of the **trivago Reference** tag that will take care of cookie set up for trv_reference;
* installation of the **trivago Conversion API** tag that will perform the confirmation of the booking.

#### Step 1.Set up new variables

Note the existing variables or create a new variables for required tag parameters.

1. Define the variables that are going to be passed to the tag and shared with trivago.
2. -N Set up the variable data for each one.

If you are already using the GTM, you could already have some of the variables available:
![Image of variables](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/variables.png)

Feel free to reuse them but make sure that the format is matching specifications here https://developer.trivago.com/conversiontracking/conversion-api.html

##### Create new variable for trv_reference cookie

We'll need to create a new variable dedicated to storing the cookie that will be updated by **trivago Reference** tag and later used by **trivago Conversion API**

1. Create new variable by navigating to **Variables** menu;
2. Click **New** under the **User-Defined Variables** section;
3. Click on **Variable** configuration card;
4. Select the variable type as a **1st-Party Cookie**;
5. Type under the **Cookie name** the value **GTM_TRV_REFERENCE_TR** 
6. Type the variable name on the top of the page as **trivago_cookie**;
![Image of cookie variable](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/trivago_cookie.png)


##### Set up the remaining variables

Other variables would require custom set up. If you already have variables in use for example like booking_id or arrival dates, you can reuse them. 
Let's go through the set up of the variable that take the value from the booking confirmation page. We'll use this page for this https://gaikanomer9.github.io/?trv_reference=c91fe358-e3c1-4c24-a427-bece84fe6658

We'll set up the **hotel** variable.

1. Create the new **User-Defined Variable** and select **DOM Element** as the type of that variable;
2. One the booking confirmation page select the id of the desired the element. (if you are using Chrome click on the element with right button and select **Inspect**![Image of settings](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/id.png)
3. Save the variable by the desired name and later use it in tag set up

#### Step 2.Configure the trivago Reference tag

Before we add trivago tag to the container we'll need to get them from **Community Template Gallery**.

##### Adding trivago tags to the workspace

1. From the GTM Workspace overview click on **Add a new tag**
2. Click on **Tag Configuration**
3. In the opened slide out "Choose tag type click on the **Discover more tag types in the Community Template Gallery**
4. Search or scroll for **trivago Conversion API** tag and click on it
5. Add the tag to the workspace by clicking **Add to workspace**
6. Check for the required permissions (in order for Conversion API to access the endpoint the usage of additional Javascript methods is needed and this requires the script injection permission from the trivago domain)
7. Repeat steps 4-6 for the **trivago Reference** tag.

##### Set up the tag

1. From the GTM Workspace overview click on **Add a new tag**;
2. Click on **Tag Configuration**;
3. Under the **Custom** section select the **trivago Reference**;
4. The default settings are storing the cookie for 30 days and using the *trv_reference* as a parameter in the URL. If it's the same for you leave these values;
5. Under the **Triggering** section select **Page view** trigger type and configure it like this:
![Image of settings cookie](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/settings.png)
6. Save the tag.

#### Step 3.Configure the trivago Conversion API tag

##### Set up the tag

1. From the GTM Workspace overview click on **Add a new tag**;
2. Click on **Tag Configuration**;
3. Under the **Custom** section select the **trivago Conversion API**;
4. Specify the api key and advertiser id provided by trivago;
5. Expand the **Booking parameters** section and select the variables for all the parameters you are going to pass;
6. For the **trv_reference** parameter fill in the variable created before (**trivago_cookie**);
7. Under the **Triggering** section select **Page view** trigger type and configure it like this:
![Image of tag trigger](https://raw.githubusercontent.com/Gaikanomer9/trivago_scripts/master/tag_trigger.png)
The value for RegEx expression is **[0-9a-fA-F]{8}\-[0-9a-fA-F]{4}\-[0-9a-fA-F]{4}\-[0-9a-fA-F]{4}\-[0-9a-fA-F]{12}**
8. Save the tag.

## Running the test

Inform trivago about implementing the GTM tag. After that we'll monitor the incoming bookings for some time and after matching the number of bookings from both sides the Conversion API could be considered implemented.
ss for submitting pull requests to us.

### Troubleshooting

If you want you can share the public container preview that would allow us to see the variables and triggers you are using. In order to do this copy the public link:

Versions -> (Select version with deployed trivago tags) 3 dots -> Share preview -> Share link inside

Send this link to your account manager and we'll help you to identify the problem.
