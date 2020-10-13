# Pipeline Expressions Cheatsheet
Tips & Tricks and Cheatsheet for Pipeline Expressions (aka SpEL) for Spinnaker

## Bracket `[]` vs Dot `.` Notations
Bracket notation ('[]'), is useful when the json key name contains spaces or periods. e.g. when parsing kubernetes annotations or labels.  `manifest["labels"]["app.kubernetes.io/name"]`

## Common Expressions

| Expression          | Description                                              |
| :---                | :----------------------------------------------------    |
| ${parameters.foo}   | accessing a parameter defined in the Configuration Stage |
| ${expression}       | sample description                                       |


## Helper Functions

| Expression                            | Description                                          |
| :---                                  | :---                                                 |
| ${#judgment("judgment stage name")}   | useful for execution options or check preconditions  |
| ${#stage("stagename})}                | get the stage json including outputs, context        |
| ${#root}                              | get the current pipeline context, useful for getting the pipeline id |


## White Listed Java classes
reference: https://spinnaker.io/reference/pipeline/expressions/#allowed-java-classes

| Expression                                                                              | Description                                           |
| :---                                                                                    | :---                                                  |
| ${(new java.util.UUID(0,0)).randomUUID()}                                               | Generate a random UUID                                |
| ${new java.text.SimpleDateFormat("yyyy-MMM-dd, hh:mm:ss").format(new java.util.Date())} | Generate a date time string of the current time       |
| ${new java.util.Random().nextInt(30)}                                                   | Generate a random number between 0 and 30             |




## Filter Maps / Collection Selection
reference: https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/expressions.html#expressions-collection-selection

Using the `.^` and `.$` notation can help filter for the first and last occurrence, respectively, of an array objects matching a particular filter. 


| Expression                              | Description                                           |
| :---                                    | :---                                                  |
| ${trigger.artifacts.^[type="git/file"]} | find the first array item that is of type="git/file", known as "collection selection"  |
|                                         |                                       |
