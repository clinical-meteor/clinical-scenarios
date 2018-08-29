# clinical:example-plugin

This is an example plugin for Meteor on FHIR (and Symptomatic) that illustrates how to create a REST endpoint, database collection, server side publication, client side subscription, and a reactive user interface.  When implemented, you can ping the REST endpoint, and it will automatically update the user interface.  


#### Clone the Example Plugin      

```bash
cd webapp/packages
git clone https://github.com/clinical-meteor/example-plugin  
```

#### Customize the Plugin      

```bash
# Step 1 - Rename package folder
packages/example-plugin

# Step 2 - Update package name, description
packages/my-plugin/package.js

# Step 3 - Customize the HelloWorld Page
packages/my-plugin/client/HelloWorldPage.jsx

# Step 4 - Update your routes if you wish
packages/my-plugin/index.jsx

# Step 5 - Edit the settings file; add custom route, etc.
packages/my-plugin/configs/settings.example.jsx
```


#### Run Meteor on FHIR with your plugin  

```bash
# add your package
meteor add foo:my-plugin
meteor npm install

# run with a custom settings file
meteor --settings packages/my-plugin/configs/settings.example.json
```

#### Example: Body Mass Index - Data Pipeline  

The BodyMassIndex calculator relies on [SMART on FHIR](http://docs.smarthealthit.org/) to fetch [FHIR Patient](https://www.hl7.org/fhir/patient.html) and [FHIR Observation](https://www.hl7.org/fhir/observation.html) resources.  We then create a [FHIR RiskAssessment](https://www.hl7.org/fhir/riskassessment.html) for obesity.  When fetching from an upstream FHIR Server, the overall data architecture and sequence diagram looks like the following.

![BodyMassIndex Data Pipeline](https://raw.githubusercontent.com/symptomatic/example-plugin/master/assets/Body%20Mass%20Index%20Calculator%20Plugin%20-%20New%20Page.png)  
