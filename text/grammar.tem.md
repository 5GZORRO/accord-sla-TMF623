This SLA, with the ID {{id}}, with the name {{name}} and href: {{href}}.

{{#with template}}It was made using template: {{name}}, {{description}}. Href: {{href}}.{{/with}}

RELATED PARTY REFS:
{{#ulist relatedParty}}
{{href}}: {{role}} ({{name}}). {{#with validFor}}Valid since {{startDateTime as "DD/MM/YYYY"}} until {{endDateTime as "DD/MM/YYYY"}}.{{/with}}
{{/ulist}}

Description:
{{description}}.

{{#with validFor}}This SLA is valid since {{startDateTime as "DD/MM/YYYY"}} until {{endDateTime as "DD/MM/YYYY"}}.{{/with}}

Current state: {{state}}.

Approved: {{approved}} on {{approvalDate as "DD/MM/YYYY"}}.

RULES:
{{#olist rule}}
{{id}} : {{metric}} - {{unit}} ({{referenceValue}}). Operator: {{operator}}, tolerance: {{tolerance}}, consequence: {{consequence}}.
{{/olist}}

version: {{version}}.
