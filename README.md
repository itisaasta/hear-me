# hear-me

Hear me helps bring your voice assistant idea to life. You can create an Alexa skill that plays a game, calls a web service, or stores data.

## You will need:
- Laptop (Mac, Windows, or Linux)
- [Amazon Web Services Account](https://aws.amazon.com/)
- [Amazon Developer Portal Account](https://developer.amazon.com/)

## This kit contains:
- Example skill templates in [python](baseSkill.py) and [Node.JS](baseSkill.js) that can be used to start any skill and add your own custom code to them
- [Example game Alexa skill](#game-alexa-skill)
    - Alexa, kids games
         - play duck duck
         - play peek a boo
         - play marco
- [Example poem reading Alexa skill (call a web service example)](#poem-reading-alexa-skill)
    - Alexa, dickinson poems
         - dickinson poems read me a poem
- [Example to-do note Alexa skill (store data example)](#save-to-do-notes-alexa-skill)
    - Alexa, million things
         - save my thing to get done "buy milk"
         - what are my things to get done

## Key concepts
- Alexa skills are built in two components: code called a function and configuration called the skill
- Alexa skill configurations are made up of intents and slots
    - Intents are the phrases that state the action the person wants to do
        - play a game
        - read a poem
        - save a todo
    - Slots are the nouns or phrases that a person is selecting to modify or detail the action
        - buy milk
        - Alaska
- Alexa functions can be written in any language - the examples provided are python and Node.js, and they are interchangeable when used with the skill configuration - if you're brand new to development, you may want to start with python

## Getting started
Basic Alexa skill development behavior is having two tabs open at a time: one with AWS lambda function and one with the developer portal Alexa configuration and testing.

### Game Alexa skill
Objective: Be able to play Duck Duck Goose, Peekaboo, or Marco Polo
1. Via the Amazon Web Services Console, create a lambda function called gameSkill in python or Node.JS
    - Function Setup
        - In a web browser, go to: https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions
        - In the top right corner, click the orange button that says *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/1.png" width="700px"/>
        - Click Blueprints, then search for *Alexa*, and click on *alexa-skills-kit-color-expert-python* for Python or *alexa-skills-kit-color-expert* for Node.JS
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/2.png" width="700px"/>
        - In the *Basic Information* section, name your function gameSkill, and for Role, select *Create new role from template(s)*, enter *alexaSkill* for Role Name, and from Policy templates list, select *Simple Microservice permissions*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/5.png" width="700px"/>
        - In the *Alexa Skills Kit trigger* section, click Disable
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/6.png" width="700px"/>
        - In the bottom right corner, click *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/7.png" width="700px"/>
    - Function Coding
        - You can edit all of your function code in the browser-based development environment
        - Copy the ARN from the top right corner - you will need this for the skill creation section
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/8.png" width="700px"/>
        - Try to experiment and write some of the code on your own - a fully working reference is available in this repo in [python](https://github.com/innovaasta/hear-me/blob/master/gameSkill.py) and [Node.js](https://github.com/innovaasta/hear-me/blob/master/gameSkill.js)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/9.png" width="700px"/>
2. Via the Amazon Developer Portal, create a skill called kidsGames
    - Skill Setup
        - In a web browser, go to: https://developer.amazon.com/alexa/console/ask
        - In the top right corner, click the blue button that says *Create Skill*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/12.png" width="700px"/>
        - Name your skill kidsGames and click the blue *Create Skill* button in the top right corner
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/13.png" width="700px"/>
        - Click the blue *Choose* button in the top right corner to keep the default *Custom* model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/14.png" width="700px"/>
    - Invocation Configuration
        - From the left menu, click invocation and set the skill invocation name to *kids games*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/15.png" width="700px"/>
    - Intent Configuration
        - From the left menu, click add and create each of the following Intents: 
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/16.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/17.png" width="700px"/>
        
    - name: DuckDuckGooseIntent
        - sample utterance: play duck duck
    - name: PeekabooIntent
        - sample utterance: play peek a boo
    - name: MarcoPoloIntent
        - sample utterance: play Marco
    
    - Endpoint Configuration
        - From the left menu, click endpoint
        - Select AWS Lambda ARN and in the Default Region field, paste in the ARN you copied from the gameSkill lambda function you created earlier (e.g. arn:aws:lambda:us-east-1:596304525112:function:gameSkill)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/18.png" width="700px"/>
    - Testing
        - Click Save Model and Build Model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/19.png" width="700px"/>
        - When the build finishes, move to the test tab
        - Click the slider on the top left of the page to enable testing for the skill and accept all messages that ask you whether it is okay to use your microphone
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/20.png" width="700px"/>
        - Click and hold the mic and say a phrase to test your skill (this is just like talking to your Echo, Dot, or Tap), such as:
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/21.png" width="700px"/>
        
    - must say first: Alexa, kids games
        - you would expect to hear "Welcome to kids games. Please say play Duck Duck, Peekaboo, or Marco."
     - then say (in separate phrases):
        - play duck duck
            - you would expect to hear "Goose"
        - play peek a boo
            - you would expect to hear "I see you"
        - play marco
            - you would expect to hear "Polo"
 
        - Sometimes Alexa has a hard time interpreting what you're saying, in which case you may need to repeat the same line again
        - If you encounter an error, take a look at the *Monitoring* tab in the AWS console for your function, then click *View logs in CloudWatch*, then click on the most recent log stream, then you can click any arrow to expand the logic that ran to get hints on where you might try to debug your issues
        - You can also copy the JSON input generated by the Alexa skill tester into your lambda skill for standalone testing
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/22.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/24.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/23.png" width="700px"/>

### Poem Reading Alexa skill
Objective: Be able to call a web service and read a poem
1. Via the Amazon Web Services Console, create a lambda function called poemSkill in python or Node.JS
    - Function Setup
        - In a web browser, go to: https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions
        - In the top right corner, click the orange button that says *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/1.png" width="700px"/>
        - Click Blueprints, then search for *Alexa*, and click on *alexa-skills-kit-color-expert-python* for Python or *alexa-skills-kit-color-expert* for Node.JS
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/2.png" width="700px"/>
        - In the *Basic Information* section, name your function poemSkill, and for Role, select *Create new role from template(s)*, enter *alexaSkill* for Role Name, and from Policy templates list, select *Simple Microservice permissions*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/5.png" width="700px"/>
        - In the *Alexa Skills Kit trigger* section, click Disable
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/6.png" width="700px"/>
        - In the bottom right corner, click *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/7.png" width="700px"/>
    - Function Coding
        - You can edit all of your function code in the browser-based development environment
        - Copy the ARN from the top right corner - you will need this for the skill creation section
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/8.png" width="700px"/>
        - Try to experiment and write some of the code on your own - a fully working reference is available in this repo in [python](https://github.com/innovaasta/hear-me/blob/master/poemSkill.py) and [Node.js](https://github.com/innovaasta/hear-me/blob/master/poemSkill.js)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/9.png" width="700px"/>
2. Via the Amazon Developer Portal, create a skill called dickinsonPoems
    - Skill Setup
        - In a web browser, go to: https://developer.amazon.com/alexa/console/ask
        - In the top right corner, click the blue button that says *Create Skill*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/12.png" width="700px"/>
        - Name your skill dickinsonPoems and click the blue *Create Skill* button in the top right corner
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/13.png" width="700px"/>
        - Click the blue *Choose* button in the top right corner to keep the default *Custom* model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/14.png" width="700px"/>
    - Invocation Configuration
        - From the left menu, click invocation and set the skill invocation name to *dickinson poems*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/15.png" width="700px"/>
    - Intent Configuration
        - From the left menu, click add and create each of the following Intents: 
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/16.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/17.png" width="700px"/>
        
    - name: GetDickinsonPoem
        - sample utterance: read me a poem
        - sample utterance: get me a poem
        - sample utterance: read me another poem
        - sample utterance: get me another poem

    - Endpoint Configuration
        - From the left menu, click endpoint
        - Select AWS Lambda ARN and in the Default Region field, paste in the ARN you copied from the poemSkill lambda function you created earlier (e.g. arn:aws:lambda:us-east-1:596304525112:function:poemSkill)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/18.png" width="700px"/>
    - Testing
        - Click Save Model and Build Model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/19.png" width="700px"/>
        - When the build finishes, move to the test tab
        - Click the slider on the top left of the page to enable testing for the skill and accept all messages that ask you whether it is okay to use your microphone
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/20.png" width="700px"/>
        - Click and hold the mic and say a phrase to test your skill (this is just like talking to your Echo, Dot, or Tap), such as:
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/21.png" width="700px"/>
        
    - NOTE: Alexa has a hard time understanding the words poem and poems - try pronouncing like poe-em and poe-ems
    - must say first: Alexa, dickinson poems
        - you would expect to hear "Welcome to Emily Dickinson Poems. Please ask for a poem by saying, Dickinson Poems read me a poem."
    - then say (in separate phrases):
        - dickinson poems read me a poem
            - you would expect to hear the reading of a random Emily Dickinson poem
                    
        - Sometimes Alexa has a hard time interpreting what you're saying, in which case you may need to repeat the same line again
        - If you encounter an error, take a look at the *Monitoring* tab in the AWS console for your function, then click *View logs in CloudWatch*, then click on the most recent log stream, then you can click any arrow to expand the logic that ran to get hints on where you might try to debug your issues
        - You can also copy the JSON input generated by the Alexa skill tester into your lambda skill for standalone testing
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/22.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/24.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/23.png" width="700px"/>

### Save to-do notes Alexa skill
Objective: Be able to store to-do notes in a database and read back all to-dos
1. Via the Amazon Web Services Console, create a DynamoDB table called todos
    - In a web browser, go to: https://console.aws.amazon.com/dynamodb/home?region=us-east-1
    - Click create table
    - <img src="https://github.com/innovaasta/hear-me/blob/master/images/10.png" width="700px"/>
    - Create a new table called todos with a partition key of todo-id
    - <img src="https://github.com/innovaasta/hear-me/blob/master/images/11.png" width="700px"/>
2. Via the Amazon Web Services Console, create a lambda function called todoSkill in python or Node.JS
    - Function Setup
        - In a web browser, go to: https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions
        - In the top right corner, click the orange button that says *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/1.png" width="700px"/>
        - Click Blueprints, then search for *Alexa*, and click on *alexa-skills-kit-color-expert-python* for Python or *alexa-skills-kit-color-expert* for Node.JS
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/2.png" width="700px"/>
        - In the *Basic Information* section, name your function todoSkill, and for Role, select *Create new role from template(s)*, enter *alexaSkill* for Role Name, and from Policy templates list, select *Simple Microservice permissions*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/5.png" width="700px"/>
        - In the *Alexa Skills Kit trigger* section, click Disable
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/6.png" width="700px"/>
        - In the bottom right corner, click *Create Function*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/7.png" width="700px"/>
    - Function Coding
        - You can edit all of your function code in the browser-based development environment
        - Copy the ARN from the top right corner - you will need this for the skill creation section
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/8.png" width="700px"/>
        - Try to experiment and write some of the code on your own - a fully working reference is available in this repo in [python](https://github.com/innovaasta/hear-me/blob/master/todoSkill.py) and [Node.js](https://github.com/innovaasta/hear-me/blob/master/todoSkill.js)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/9.png" width="700px"/>
3. Via the Amazon Developer Portal, create a skill called millionThings
    - Skill Setup
        - In a web browser, go to: https://developer.amazon.com/alexa/console/ask
        - In the top right corner, click the blue button that says *Create Skill*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/12.png" width="700px"/>
        - Name your skill millionThings and click the blue *Create Skill* button in the top right corner
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/13.png" width="700px"/>
        - Click the blue *Choose* button in the top right corner to keep the default *Custom* model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/14.png" width="700px"/>
    - Invocation Configuration
        - From the left menu, click invocation and set the skill invocation name to *million things*
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/15.png" width="700px"/>
    - Intent Configuration
        - From the left menu, click add and create each of the following Intents: 
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/16.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/17.png" width="700px"/>
        
    - name: SaveTodo
        - sample utterance: save my thing to get done {buy milk|todo}
    - name: GetTodo
        - sample utterance: What are my things to get done
                
    - Slot Configuration
        - From the left menu, click add and create each of the following Slots:
            - name: todo
                - type: AMAZON.LITERAL
    - Endpoint Configuration
        - From the left menu, click endpoint
        - Select AWS Lambda ARN and in the Default Region field, paste in the ARN you copied from the gameSkill lambda function you created earlier (e.g. arn:aws:lambda:us-east-1:596304525112:function:todoSkill)
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/18.png" width="700px"/>
    - Testing
        - Click Save Model and Build Model
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/19.png" width="700px"/>
        - When the build finishes, move to the test tab
        - Click the slider on the top left of the page to enable testing for the skill and accept all messages that ask you whether it is okay to use your microphone
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/20.png" width="700px"/>
        - Click and hold the mic and say a phrase to test your skill (this is just like talking to your Echo, Dot, or Tap), such as:
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/21.png" width="700px"/>

    - must say first: Alexa, million things
        - you would expect to hear "Welcome to Million Things. Please add a to do by saying save my thing to get done or get all to do's by saying what are my things to get done."
    - then say (in separate phrases):
        - save my thing to get done "buy milk"
            - you would expect to hear "To do saved"
        - what are my things to get done
            - you would expect to hear "buy milk"
                    
        - Sometimes Alexa has a hard time interpreting what you're saying, in which case you may need to repeat the same line again
        - If you encounter an error, take a look at the *Monitoring* tab in the AWS console for your function, then click *View logs in CloudWatch*, then click on the most recent log stream, then you can click any arrow to expand the logic that ran to get hints on where you might try to debug your issues
        - You can also copy the JSON input generated by the Alexa skill tester into your lambda skill for standalone testing
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/22.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/24.png" width="700px"/>
        - <img src="https://github.com/innovaasta/hear-me/blob/master/images/23.png" width="700px"/>

## Useful references
- [Amazon Web Services](https://aws.amazon.com/)
- [Amazon Developer Portal](https://developer.amazon.com/)
- [Alexa Simulator](https://echosim.io/)