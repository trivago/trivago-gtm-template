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
{List of params and example of how to setup it}

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
