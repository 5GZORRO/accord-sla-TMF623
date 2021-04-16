This SLA, with the ID {{id}}, with the name {{name}} and href: {{href}}.

{{#with template}}Was made using template {{name}}, {{description}} --> {{href}}.{{/with}}

RELATED PARTY REFS:
{{#ulist relatedParty}}
{{href}}: {{role}} ({{name}}). {{#with validFor}}Valid since {{startTime as "DD/MM/YYYY"}} until {{endTime as "DD/MM/YYYY"}}.{{/with}}
{{/ulist}}

Description:
{{description}}.

{{#with validFor}}This SLA is valid since {{startTime as "DD/MM/YYYY"}} until {{endTime as "DD/MM/YYYY"}}.{{/with}}

Current state: {{state}}.

Approved: {{approved}} -> {{approvalDate as "DD/MM/YYYY"}}.

RULES:
{{#olist rule}}
{{id}} : {{metric}} - {{unit}} ({{referenceValue}}). Operator: {{operator}}, tolerance: {{tolerance}}, consequence: {{consequence}}.
{{/olist}}

version: {{version}}.
