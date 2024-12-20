# Technical test - Cyril Plancke, 2024-11-36 18h50

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug : 
 - Sign up to the app
 - Create at least 2 others users on people page ( not with signup ) 
 - Edit these profiles and add aditional information 
 - Create a project
 - Input some information about the project
 - Input some activities to track your work in the good project
  
Then, see what happens in the app and fix the bug you found doing that.

## Then
Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions : 
- What bugs did you find ? How did you solve these and why ? 
  - 1. Warning: Can't perform a React state update on an unmounted component. This is a no-op, but it indicates a memory leak in your application. To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.
    Solution : check if component is mounted, and I used useRef()

  - 2. Name input is disabled
  Solution : changed to enabled="true"
  
  - 3. The Update button was not triggered because a onChange was iused instead of a onClick, and is was not specified as type="button" 
  Solution : I used onClick, and added type="button" in the HTML tag
  
  - 4. On each input of the New user dialog box: "A component is changing an uncontrolled input of type undefined to be controlled. Input elements should not switch from uncontrolled to controlled (or vice versa)."
  Solution : I had to set default values for each field to set a default type, that way React knows which type to expect : 
             > initialValues={{username: '', email: '', password:''}}
  I also changed the default availability from 'not available' to 'available' tocheck if it was working.

  - 5. Missing type for new project form on "Create" button (same solution as point 3)

  - 6. project.name undefined : cause a crash from dev tool
   Solution :  dans le span : {project.name?.toString()||'[find a project name]'}

  - 7. Errorwhen accessing project Edit : error 500
    solution : in api/src/controllers/project.js : 
  at line 22 : changed find to findOne

  - 8. temps dépassé pour d'autres bugs...

2.
- Which feature did you develop and why ? 
Corrections mineures

- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ? 
Very well organised code, as I has no problem finding files based on the console errors
