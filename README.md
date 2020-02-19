# trivago GTM Template

trivago GTM template implementation for Conversion API connection.

## Support and questions

If you have questions about the installation process or not sure about anything feel free to get in touch via email: nikita.zavyalov@trivago.com

## Getting Started

These instructions will help you integrate trivago template as a new tag for GTM.

For more detailed documentation please reffer to the WIKI for this project [here](https://github.com/trivago/trivago-gtm-template/wiki) 

[Getting started](https://github.com/trivago/trivago-gtm-template/wiki/Getting-started)

Installation
1. [Adding tags from Community Template Gallery](https://github.com/trivago/trivago-gtm-template/wiki/Adding-tags-from-Community-Template-Gallery)
2. [Setting up variables](https://github.com/trivago/trivago-gtm-template/wiki/Setting-up-variables)
3. [Installing the trivago Reference tag](https://github.com/trivago/trivago-gtm-template/wiki/Installing-trivago-Reference-tag)
4. [Installing trivago Conversion API tag](https://github.com/trivago/trivago-gtm-template/wiki/Installing-trivago-Conversion-API-tag)

[Testing installation and publishing tags](https://github.com/trivago/trivago-gtm-template/wiki/Testing-the-installation)

[Updating tags](https://github.com/trivago/trivago-gtm-template/wiki/Updating-the-Tag)

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

For detailed instructions on how to set variables and tags up please refer to the [documentation](https://github.com/trivago/trivago-gtm-template/wiki) 


## Approving the implementation

Inform trivago about implementing the GTM tag. After that we'll monitor the incoming bookings for some time and after matching the number of bookings from both sides the Conversion API could be considered implemented.

### Troubleshooting

If you want you can share the public container preview that would allow us to see the variables and triggers you are using. In order to do this copy the public link:

Versions -> (Select version with deployed trivago tags) 3 dots -> Share preview -> Share link inside

Send this link to your account manager and we'll help you to identify the problem.
