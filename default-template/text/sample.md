This SLA, with the ID "123444", with the name "HighSpeedDataSLA" and href: "http/www.acme.com/SlaManagement/sla/123444".

It was made using template: "DataSLATemplate", "basic template forData SLA". Href: "http/www.acme.com/slaManagement/slaTemplate/42".

RELATED PARTY REFS:

- "http://": "SLAProvider" ("SLAProvider1"). Valid since 10/03/2010 until 09/08/2030.
- "http://": "SLAConsumer" ("SLAConsumer1"). Valid since 10/03/2015 until 09/08/2040.
- "http://": "SLAAuditor" ("SLAAuditor1"). Valid since 10/03/2013 until 09/08/2020.
- "http://": "SLABusinessBroker" ("SLABusinessBroker1"). Valid since 10/03/2009 until 09/08/2025.
- "http://": "SLATechnicalBroker" ("SLATechnicalBroker1"). Valid since 10/03/2008 until 09/08/2023.
- "http://": "ThirdPartySLAManager" ("ThirdPartySLAManager1"). Valid since 10/03/2011 until 09/08/2022.
- "http://": "EndUser" ("EndUser1"). Valid since 10/03/2012 until 09/08/2029.

Description:
"SLA for high speed data.".

This SLA is valid since 19/04/2013 until 21/04/2013.

Current state: "closed".

Approved: true on 25/12/2222.

RULES:

1. "availability" : "http://www.provider.com/metrics/availability" - "%" ("99.95"). Operator: GREATER, tolerance: "0.05", consequence: "http://www.provider.com/contract/claus/30".
2. "response_time" : "http://www.provider.com/metrics/response-time" - "milliseconds" ("80"). Operator: EQUAL, tolerance: "15", consequence: "Extra credit at the end of the billing cycle".

version: "0.1".
