# Setup Instructions

These instructions cover how to set up the experimental Splunk dashpub project to create a public-facing dashboard.  
This uses the [`featherbear/splunk-dashpub`](https://github.com/featherbear/splunk-dashpub) fork of [`splunk/dashpub`](https://github.com/splunk/dashpub) which better handles malformed / empty SPL queries in Dashboard elements.  
Also the `yarn.lock` issue is fixed

## Pre-requisites

### Splunk

* splunkd port (HTTPS 8089) is exposed to the Dashpub host
* The Splunk Enterprise Dashboards Beta (`splunk-dashboard-app`) app is installed on the Splunk instance

### Machine running dashpub 

* Node.js version 12 or higher is installed
* The splunkd port of the Splunk device is accessible

## Steps

**1** Create a Splunk user with read-only permissions to interact with the

**2** Use the Splunk Enterprise Dashboards Beta application to create the dashboards.  
Do ___NOT___ use the `grid` layout

**3** Initialise the project.  
`npx featherbear/splunk-dashpub init`  

Connect to the splunkd address with the template `https://YOUR_HOSTNAME_HERE:8089`.  
You can then enter the user details created from _step 1_.  
Then select the dashboards to show in the dashpub appplication

**(4)** If you want Dashpub to use static/offline data - inside the newly created project folder, edit the created `package.json` file.  
Find the the `dashpub["settings"]["useDataSnapshots"]` key and set it to `true`.

# Deployment Instructions

(Perform these steps for every new data update)

**1** Update the snapshot  
`npx featherbear/splunk-dashpub update`  

**2** Build the dashpub application  
`npm run build`

**3** Run the dashpub server  
`npm run start`
