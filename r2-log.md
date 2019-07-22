# 100DaysOfCode Log - Round 2 - Mark Krake (@metas-mk)

The log of my 2nd Round of #100DaysOfCode challenge. Started on [July 19, Friday, 2019].

## Log
In my first life I was a COBOl and Mainframe Software Developer. Being a Product Owner and Requirements engineer in the last decade, I did not code anymore and found out that I was missing it like hell. I made a plan to get back into coding frequently and am now on a mission learning JavaScript and ReactJS. I started my personal #100DaysOfCode challenge on March 24th 2019 but only logged my daily progress via Twitter (@markkrake). I'm starting the 2nd round an will log my progress here.

### R2D0 - July 19th, 2019
- Setup my git repository to log my 2nd round progress of my #100DaysOfCode challenge

### R2D1 - July 20th, 2019
#### How to Setup ESLint for my project in VSCode?
- ```cd``` into your  ```coding-repository```
- ```npm init -y```
- ```npm install -D eslint eslint-config-standard eslint-plugin-import eslint-plugin-node eslint-plugin-promise eslint-plugin-standard```
- create ```.estlintrc.js``` with ```module.exports = {"extends":"standard"};
- In VSCode make sure that ESLint is installed, id not then install it and restart VSCode

#### How to push your new local project to a GitHub Reporitory
- I started a new git project locally and decided to also push this to GitHub to allow to track my progress on that too. Here is how I did this https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line

#### ReactJS learning and coding
- Learning JSX in theory and practical coding. Started with building components.

### R2D2 - July 21st, 2019
#### Quick styling for free - Semantic UI
- checked out Sematic UI https://semantic-ui.com/
- a Free and Open Source development development framework that helps create beautiful, responsive layouts using human-friendly HTML
- just copied the semantic.min.css ling from https://cdnjs.com/libraries/semantic-ui and added to index.html as stylesheet
- Using it for my component styling when lerning ReactJS

#### First ReactJS Component with a Naive Approach
- Creating a ReactJS component for comments with a naive approach (all comments in 1 JSX div)

#### Faker.js
- Using Faker.js to generate massive amounts of realistic fake data in Node.js and the browser during the development phase of my project (https://github.com/marak/Faker.js/).
- ```npm install --save faker```

#### Having issues starting local webserver
- After install of Faker.js the local websever did not want to start anymore. I deleted the node_modules folder of my project and did a fresh ```npm install```. After that used ```npm start``` to try again, and worked.

### R2D3 - July 22nd, 2019
#### Deduplicating JSX content, component nesting
- refactoring JSX content and extracting to an own component ```CommentDetails.js```
- coding convention: Components are written with UpperCamelCase
- joined component with main App via ```export default``` and ```import```
- using the component as JSX tag ``` ``` in render method of the main App

#### Using react props system
- component hierarchy, parent component, child components or children
- props = properties
- props: system for passing data from a parent component to a child component
  - goal is to customize or configure a child component
  - provide information from parent to child (via JSX property) e.g. ```<CommentDetails date="Today 6:05PM" />```
  - consume infomation in child (via props argument object) e.g. ```{props.date}```
