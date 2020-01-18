# Getting Started with Serverless

## Hello World

- go to *[IBM Cloud Functions](https://cloud.ibm.com/functions/)*
- click on *[Actions](https://cloud.ibm.com/functions/actions)*
- click on the blue *[Create](https://cloud.ibm.com/functions/create/action)* button
- enter an *Action Name*, e.g. *hello-world-web-action*
- click on *Create*
- click on *Invoke*, you should see the result:
~~~~
Results:

{
  "message": "Hello World"
}	
~~~~

Congratulations!

## Using Parameters
- scroll up and replace the code with
~~~~
function main({name}) {
 var msg = 'You did not tell me who you are.';
 if (name) {
   msg = `Hello, ${name}!`
 }
 return {msg}
}
~~~~
- Click on *Save* and *Invoke*; we did not provide a parameter so far, the initial value of *msg is returned:
~~~~
{
  "msg": "You did not tell me who you are."
}
~~~~
- scroll up and click on *Change Input*
- replace the content with `{ "name": "Hans"}`
- click on *Save* and *Invoke*; as we provided the name parameter, it is returned by this action as part of the variable *msg*:
~~~~
{
  "msg": "Hello, Hans!"
}
~~~~

## Turning this Action into a Web Action

~~~~
function main({name}) {
 var msg = 'You did not tell me who you are.';
 if (name) {
   msg = `Hello, ${name}!`
 }
 return {body: `<html><body><h3>${msg}</h3></body></html>`}
}
~~~~

References:
- https://cloud.ibm.com/docs/openwhisk?topic=cloud-functions-actions_web
