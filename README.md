# DataPrivacyComplianceAPI

## Project Overview

This is a web service (a REST API) that encodes data privacy and protection laws from around the world and returns risk and compliance assessments regarding the proposed use of a person's personal data.  

Who would want to use this API?  Anyone considering processing, publishing, storing, deleting, or transferring someone else's personal data or personally identifiable information (PII).  

There are *numerous* laws around the world that govern what can and can't be done with someone's personal data. In the European Union, there's the Data Protection Directive and the proposed General Data Protection Regulation, as well as numerous other treaties, regulations, and court opinions governing personal data.  In the U.S., there are dozens of federal regulations pertaining to personal data, such as the Health Information Portability and Accountability Act, the Online Privacy Protection Act, and the Electronic Communications Privacy Act.  Additionally, many U.S. states have their own laws, and common law principles such as tort and libel apply.  In Australia, there's the Australian Federal Privacy Act.  In Canada, the Personal Information Protection and Electronic Documents Act.  The UK has the Data Protection Act 1998.  France, Switzerland, India, Nigeria, and Pakistan all have laws that apply to personal data.  And that's just scratching the surface. 




## Input/Output

Here's a sample API call and response to give you a sense of the input and output of the web service.  This project does not contain a human-centered user interface; only a REST API.  

### Sample REST call

```
https://<host>/privacy_API?IntendedActivities=Processing&SubjectCountry=Croatia&SubjectType=Natural%20person&ControllerType=Corporation&ProcessorType=Corporation&ControllerCountry=Croatia&ProcessorCountry=x&RecipientCountry=x&SubjectAge=8&DataContent=Criminal%20history&DataContent=Genetic&Source=Data%20subject
```

### Sample JSON repsonse

```
{
    "assumptions": [
        "RecipientType = Corporation",
        "Contents = {}",
        "ProcessingPurposes = {}",
        "CollectionPurposes = {}",
        "Consents = {}",
        "StudentQ = False"
    ],
    "overallRisk": {
        "riskPercentage": 1.0,
        "colorCode": "Red",
        "text": "Out of compliance"
    },
    "regulationsChecked": [
        {
            "name": "EU General Data Protection Directive (proposed)",
            "applicable": true,
            "riskPercentage": 1.0,
            "riskFactors": [
                "Art. 8 - Processing of personal data of a child",
                "Art. 6 - Lawfulness of processing",
                "Art. 33 - Data protection impact assessment"
            ]
        }
    ],
    "processingTimeInMS": 0.311
}
```

## Project Scope

## Contributing

Contributions are welcome and this project will be run in a spirit of respectful cooperation.  Numerous countries around the world have data privacy laws, so this is a potentially large undertaking and I'm hoping for a diverse and dispersed group of contributors.

The project is written in the [Wolfram Language](https://www.wolfram.com/language/) (formerly called Mathematica).  Admittedly, this is an offbeat language to use in an open source project.  However, it's a deep, broad, and beautiful language and I hop you'll take the opportunity to learn more about it.  It is truly a joy to use.

You can use the Wolfram Language for free by [registering with Wolfram Research](https://user.wolfram.com/wolframid/registration/cloud).  Then you can upload the .nb (notebook) file to the Wolfram cloud and tinker with it there.

If you have any questions, feel free to contact me at mpoulshock@gmail.com.


