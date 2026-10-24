I want to create a factory for generating code.
The factory should be a skill that triggers multiple agents and skills.
The factory should be able to generate code for different programming languages.

the factory should work like a full agile team.

The skill should start with asking the user what he wants to create.
This should be done using the grilling skill (found here https://github.com/mattpocock/skills/blob/release/v1.3/skills/productivity/grilling/SKILL.md)
This skill should create a mental map of what the user wants to create and explore the user's requirements.

A glossary should be created to define the terms used.

Once the feature is mapped out, the skill should create spec file based on the mental map created by the grilling skill.
this spec file should hold the requirements for the feature. the acceptance criteria should be written in Gerkin (BDD)

a human should review the spec file and approve it before the factory starts generating code.

next a planning agent should create a plan of what to implement.
a skill need to be created for this, the skill should split up the tasks so the context of the agent implementing it stays under 150 000 tokens.

it should then implement first the scaffolding of the feature. meaning the classes, the objects, the modules, all it needs to be able to start, it's a Techincal design so no logic should be written.

Then the tests should be create based on the acceptance criteria. (we are working in TDD/BDD)

the test should fail first since we only have the boilerplate code.

Then an agent should implement the feature based on the plan created by the planning agent and the test cases.

once it passes an other agent should review the code and approve it. this reviewer should check the code that is writen against the spec file.
an other agents checks if the code that is written follows the coding standards and best practices.

After both are happy a PR should be created and a human reviewer should approve it.

After it is implemented an agents should check what he did wrong and suggest skills or guideline for himself to be better the next time.
A human needs to review these guidelines and suggest improvements.
