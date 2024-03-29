[![accord project](https://img.shields.io/badge/powered%20by-accord%20project-19C6C8.svg)](https://www.accordproject.org/)

https://confluence.i2cat.net/display/5GP/SLA+format+and+metric+proposals

# Accord Protocol Template: sla-zorro

The is an Accord Protocol Template. Executing the clause will simply echo back the text that occurs after the string `Hello` prepended to text that is passed in the request.

### Parse

Use the `cicero parse` command to load a template from a directory on disk and then use it to parse input text, echoing the result of parsing. If the input text is valid the parsing result will be a JSON serialized instance of the Template Mode:

Sample template.tem:

```
Name of the person to greet: [{name}].
Thank you!
```

Sample.txt:

```
Name of the person to greet: "Dan".
Thank you!
```

```
cicero parse --template ./sla-zorro/ --dsl ./sla-zorro/sample.txt
Setting clause data: {"$class":"io.clause.helloworld.MyContract","name":"Dan"}
```

Or, attempting to parse invalid data will result in line and column information for the syntax error.

Sample.txt:

```
FUBAR Name of the person to greet: "Dan".
Thank you!
```

```
{ Error: invalid syntax at line 1 col 1:

  FUBAR  Name of the person to greet: "Dan".
  ^
Unexpected "F"
```

### Execute

Use the `cicero execute` command to load a template from a directory on disk, instantiate a clause based on input text, and then invoke the clause using an incoming JSON payload.

```
data.json:
{
   "$class": "sla.zorro.templates.MyRequest",
   "input": "World"
}
```

```
cicero execute --template ./sla-zorro/ --dsl ./sla-zorro/sample.txt --data ./sla-zorro/data.json
```

The results of execution (a JSON serialized object) are displayed. They include:

- Details of the clause executed (name, version, SHA256 hash of clause data)
- The incoming request object
- The output response object

```
{
   "clause":"helloworld@0.0.3-c8d9e40fe7c5a479d1a80bce2d2fdc3c8a240ceb44a031d38cbd619e9b795b60",
   "request":{
      "$class":"sla.zorro.templates.Request",
      "input":"World"
   },
   "response":{
      "$class":"sla.zorro.templates.Response",
      "output":"Hello Dan World",
      "transactionId":"cf1dabb5-d604-4ffa-8a87-8333e77a735a",
      "timestamp":"2017-10-31T10:47:42.055Z"
   }
}
```
