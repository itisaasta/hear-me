# hear-me

Hear me helps bring your voice assistant idea to life. You can create an Alexa skill that plays a game, calls a web service, or stores data.

## You will need:
- Laptop (Mac, Windows, or Linux)
- [Amazon Web Services Account](https://aws.amazon.com/)
- [Amazon Developer Portal Account](https://developer.amazon.com/)

## This kit contains:
- Example game Alexa skill
- Example poem reading Alexa skill (call a web service example)
- Example to-do note Alexa skill (store data example)

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
        - Name your skill kidsGames and click the blue *Create Skill* button in the top right corner
        - Click the blue *Choose* button in the top right corner to keep the default *Custom* model
    - Intent Configuration
        - From the left menu, click add and create each of the following Intents
            - name: DuckDuckGooseIntent
                - sample utterance: play duck duck
            - name: PeekabooIntent
                - sample utterance: play peek a boo
            - name: MarcoPoloIntent
                - sample utterance: play Marco
    - Endpoint Configuration
        - From the left menu, click endpoint
        - Select AWS Lambda ARN and in the Default Region field, paste in the ARN you copied from the gameSkill lambda function you created earlier (e.g. arn:aws:lambda:us-east-1:596304525112:function:gameSkill)
    - Testing
        - Click Save Model and Build Model
        - When the build finishes, move to the test tab
        - Click the slider on the top left of the page to enable testing for the skill and accept all messages that ask you whether it is okay to use your microphone
        - Click and hold the mic and say a phrase to test your skill (this is just like talking to your Echo, Dot, or Tap), such as:
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
### Poem Reading Alexa skill (call a web service example)
Objective: Be able to call a web service and read a poem
1. Via the Amazon Web Services Console, create a lambda function called poemSkill in python or Node.JS
2. Via the Amazon Developer Portal, create a skill called dickinsonPoems
    - Intents
        - GetDickinsonPoem
            - read me a poem
            - get me a poem
            - read me another poem
            - get me another poem

### Save to-do notes Alexa skill (store data example)
Objective: Be able to store to-do notes in a database
1. Via the Amazon Web Services Console, create a lambda function called todoSkill in python or Node.JS
2. Via the Amazon Developer Portal, create a skill called myTodos

## Useful references
- [Amazon Web Services](https://aws.amazon.com/)
- [Amazon Developer Portal](https://developer.amazon.com/)
- [Alexa Simulator](https://echosim.io/)
- [Alexa Skill Python Tutorial](https://developer.amazon.com/alexa-skills-kit/alexa-skill-python-tutorial)