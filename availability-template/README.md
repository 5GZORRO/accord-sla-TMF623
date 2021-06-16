[![accord project](https://img.shields.io/badge/powered%20by-accord%20project-19C6C8.svg)](https://www.accordproject.org/)

https://confluence.i2cat.net/display/5GP/SLA+format+and+metric+proposals

# Accord Protocol Template: availability-template

The is an Accord Protocol Template for a basic availability SLA

# Design Decisions

## Model changes

### SLA Model
Removed fields belonging to the TMF SLA models that are not relevant to the prose.  As such when a TMF SLA model is loaded from the SLA Manager this should be mapped to an object that has the subset of properties that are required by this contract model.

#### SLA.consequence
Rather than setting a href value to some repository of consequences, the current implementation expects the consequence to be a value describing a number of service credits that should be awarded.  It may be decided that this is not flexible enough, but this is the current implementaiton. 

### Violation Model
The same goes for Violations, the accord contract doesn't have or need details regarding the SLARef (and other properties) as such the Violation model emitted in an obligation should be mapped to the larger full TMF Violation model and have these additional properties set before being published for subscribing apps to consume.

### Model mapping principle
With the above in mind it is expected that the portal (or client executing the cicero/ergo logic) will perform the following tasks

**For Template creation**
Generate an empty model that aligns with the contract model with preset values for version, a single related party (provider) and pass this into the template editor

e.g.
```{
  "name": "",
  "description": "",
  "version": "0.0.1",
  "validFor": {   
    "startDateTime": "2013-04-19T00:00:00.000+01:00",
    "endDateTime": "2013-04-21T00:00:00.000+01:00"
  },
  "relatedParty": [
    {
      "$class": "sla.zorro.templates.availability_template.RelatedPartyRef",
      "href": "http://",
      "role": "SLAProvider",
      "name": "SLAProvider1",
      "validFor": {
        "$class": "sla.zorro.templates.availability_template.TimePeriod",
        "startDateTime": "2010-03-10T03:00:00.000+01:00",
        "endDateTime": "2030-08-09T00:00:00.000+01:00"
      }
    }
  ],
  "rule": [
  ]
}
```
**When Saving the SLA**
Take the model populated in the editor and map to the full TMF Model .  Either set the values that have been loaded from the SLA Manager i.e. if performing an update, or by newing up an empty TMF Model, mapping the accord mdel values to it, and set any other required field values before submitting to the SLA Manager.

**Emitted SLA Violations**
Follow the principles as per above, map the Violation emitted to a full TMF Violation model, set any required fields and then submit to whatever API/queue as neccessary.

### Parse

Use the `cicero parse --template availability-template` command to load a template from a directory on disk and then use it to parse input text, echoing the result of parsing. If the input text is valid the parsing result will be a JSON serialized instance of the Template Mode:

### Generate .cta archive

Use the `cicero archive --template availability-template` command to generate a .cta

### Trigger

Use the `cicero trigger` command to load a template from a directory on disk, instantiate a clause based on input text, and then invoke the clause using an incoming JSON payload.  By default it will use the `text/sample.md`, `data.json` and `request.json` to execute the request, but you can specify alternative files (see `cicero trigger --help` for how)

`cicero trigger --template availability-template`

The results of execution (a JSON serialized object) are displayed. They include:

- Details of the clause executed (name, version, SHA256 hash of clause data)
- The incoming request object
- The output response object

