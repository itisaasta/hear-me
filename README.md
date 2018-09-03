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
### Game Alexa skill
Objective: Be able to play Duck Duck Goose, Peekaboo, or Marco Polo
1. Via the Amazon Web Services Console, create a lambda function called gameSkill in python or Node.JS
    - For Role, select "Create new role from template(s)" and enter "alexaSkill" for Role Name and from Policy templates list, select "Simple Microservice permissions"
    - Under "Designer->add triggers" select "Alexa Skills Kit" 
2. Via the Amazon Developer Portal, create a skill called kidsGames
    - Intents
        - DuckDuckGooseIntent
            - play duck duck
        - PeekabooIntent
            - play peek a boo
        - MarcoPoloIntent
            - play Marco
    - Endpoint
        - Copy ARN from "gameSkill" lambda function (e.g. arn:aws:lambda:us-east-1:596304525112:function:gameSkill)
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