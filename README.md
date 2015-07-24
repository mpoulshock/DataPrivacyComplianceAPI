# Data Privacy Compliance API

## Project Overview

This is a web service (a REST API) that encodes data privacy and protection laws from around the world and returns risk and compliance assessments regarding the proposed use of a person's personal data.  

Who would want to use this API?  Anyone considering processing, publishing, storing, deleting, or transferring someone else's personal data or personally identifiable information (PII).  

There are *numerous* laws around the world that govern what can and can't be done with someone's personal data. In the European Union, there's the Data Protection Directive and the proposed General Data Protection Regulation, as well as numerous other treaties, regulations, and court opinions governing personal data.  In the U.S., there are dozens of federal regulations pertaining to personal data, such as the Health Information Portability and Accountability Act, the Online Privacy Protection Act, and the Electronic Communications Privacy Act.  Additionally, many U.S. states have their own laws, and common law principles such as tort and libel apply.  In Australia, there's the Australian Federal Privacy Act.  In Canada, the Personal Information Protection and Electronic Documents Act.  The UK has the Data Protection Act of 1998.  France, Switzerland, India, Nigeria, and Pakistan all have laws that apply to personal data.  And that's just scratching the surface. 

Since information can go global in milliseconds, it's critical that people responsible for handling and processing personal data ensure that they're in compliance with this transnational body of legal rules.

This API takes, as input, information about a proposed use of personal data.  It then determines which laws apply to that situation and, of those that apply, which are at risk of being violated.  The result is a probabilistic risk assessment that flags transactions that are likely to be out of compliance.  The API response identifies the specific provisions of law that might be of concern, in order to expedite a manual review of the proposed transaction.


## Input/Output

Here's a sample API call and response to give you a sense of the input and output of the web service.  This project does not contain a human-centered user interface; only a REST API.  

### Sample REST call

```
https://<host>/privacy_API?IntendedActivities=Processing&SubjectCountry=Croatia&SubjectType=Natural%20person&ControllerType=Corporation&ProcessorType=Corporation&ControllerCountry=Croatia&SubjectAge=18&DataContent=Criminal%20history&DataContent=Genetic&Source=Data%20subject
```

### Sample JSON repsonse

```
{
    "assumptions": [
        "RecipientType = Corporation",
        "StudentQ = False"
    ],
    "overallRisk": {
        "riskPercentage": 1.0,
        "colorCode": "Red",
        "text": "Out of compliance"
    },
    "regulationsChecked": [
        {
            "name": "General Data Protection Directive (EU, proposed)",
            "citation": "http://ec.europa.eu/justice/data-protection/document/review2012/com_2012_11_en.pdf",
            "applicable": true,
            "riskPercentage": 1.0,
            "riskFactors": [
                "Art. 8 - Processing of personal data of a child",
                "Art. 6 - Lawfulness of processing",
                "Art. 33 - Data protection impact assessment"
            ]
        },
        {
            "name": "Children's Online Privacy Protection Act (U.S.)",
            "citation": "16 C.F.R. Part 312",
            "applicable": true,
            "riskPercentage": 1.0,
            "riskFactors": [
                "Sec. 312.5 - Parental consent to collection, use, or disclosure of child's personal information",
                "Sec. 312.6 - Right of parent to review personal information provided by a child",
                "Sec. 312.4 - Obligation to provide notice to parent"
            ]
        }
    ],
    "processingTimeInMS": 0.311
}
```

## Project Scope

As described above, there's a lot of legal ground that this API can cover.  In general terms, the project scope is for the API to include:

1. All laws pertaining to the use of personal data,
2. In all jurisdictions around the world, and
3. Keeping the rules updated as regulations change.

I'm thinking of approaching this in phases:

### Phase 1

* Can the data be collected?
* Can the data be processed?
* Can the data be transmitted/transferred?
* Can the data be published?
* Can the data be stored?
* Can/must the data be deleted?  When?
* Must the data be anonymized or pseudonymized?
* Might there be a fundamental rights conflict?
* Is advance notice to the data subject required?
* Must the data subject be given any control over their information?

### Phase 2

* Use of data by government agencies (non-law enforcement)
* Reporting of data breaches

### Out of scope

* Data collection by law enforcement / national security
* Data security / requirements for information (IT) systems
* Processing credit card data (PCI)
* The right to be forgotten

## Disclaimer

The use of this code is subject to a [modified MIT license](https://github.com/mpoulshock/DataPrivacyComplianceAPI/blob/master/LICENSE).  The license states that this program is not a perfect reflection of the applicable laws, that the user is responsible for undertaking their own legal analysis, and that the program is not a substitute for the advice of an attorney.

This API creates a probabilistic assessment of compliance risk.  Even when the API says that the risk of noncompliance is low, it could be wrong, as the encoded regulations are typically a rough approximation of the law itself.  The API response indicates which regulations were checked, which ones apply, and which ones are of concern.  Use your common sense when interpreting and relying upon these results.

## Contributing

Contributions are welcome and this project will be moderated in a spirit of respectful cooperation.  Numerous countries around the world have data privacy laws, so this is a potentially large undertaking and I'm hoping for a diverse and dispersed group of contributors.

The project is written in the [Wolfram Language](https://www.wolfram.com/language/) (formerly called Mathematica).  Admittedly, this is an offbeat language to use in an open source project.  However, it's a deep, broad, and beautiful language and I hope you'll take the opportunity to learn more about it.  It's a joy to use.

You can use the Wolfram Language for free by [registering with Wolfram Research](https://user.wolfram.com/wolframid/registration/cloud).  Then you can upload the .nb [source code file](https://github.com/mpoulshock/DataPrivacyComplianceAPI/tree/master/Source) to the Wolfram cloud and tinker with it there.

To view a PDF version of the source code, [look here](https://github.com/mpoulshock/DataPrivacyComplianceAPI/blob/master/Documentation/Data%20privacy%20compliance.pdf).  It's easier to read than the .nb file, which doesn't render well in Github.

If you have any questions, feel free to contact me at mpoulshock@gmail.com.


