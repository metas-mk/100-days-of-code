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
- just copied the semantic.min.css link from https://cdnjs.com/libraries/semantic-ui and added to index.html as stylesheet
- Using it for my component styling when lerning ReactJS

#### First ReactJS Component with a Naive Approach
- Creating a ReactJS component for comments with a naive approach (all comments in 1 JSX div)

#### Faker.js
- Using Faker.js to generate massive amounts of realistic fake data in Node.js and the browser during the development phase of my project (https://github.com/marak/Faker.js/).
- ```npm install --save faker```

#### Having issues starting local webserver
- After install of Faker.js the local websever did not want to start anymore. I deleted the node_modules folder of my project and did a fresh ```npm install```. After that used ```npm start``` to try again, and worked.

### R2D3 - July 22nd, 2019
#### new git command
- first time used ```git commit --amend```
  - allows you to adjust the last commit message directly via editor 

#### Deduplicating JSX content, component nesting
- refactoring JSX content and extracting to an own component ```CommentDetails.js```
- coding convention: Components are written with UpperCamelCase
- joined component with main App via ```export default``` and ```import```
- using the component as JSX tag ``` ``` in render method of the main App

#### Props in a nutshell: Using react props system
- component hierarchy, parent component, child components or children
- props = properties
- props: system for passing data from a parent component to a child component
  - goal is to customize or configure a child component
  - provide information from parent to child (via JSX property) e.g. ```<CommentDetails date="Today 6:05PM" />```
  - consume infomation in child (via props argument object) e.g. ```{props.date}```

### R2D4 - July 23rd, 2019
#### What is props validation?
- Runtime type checking for React props and similar objects.
- during debugging of metasfresh-webui-frontend I came past an eslint warning ```... is missing in props validation```
  - documentation here https://www.npmjs.com/package/prop-types

#### Component Reuse ReactJS
- component nesting: a component can be shown inside of another
- component reusability: components shall be easily reusable through out an application
- component configuration: a component shall be configurable when it's created

#### Nesting components & props.children
- wrapped the comments component into an approval component via jsx
- used ```props.children``` to consume the nested component

### R2D5 - July 24th, 2019
#### Function based vs. class based components
- function based: good for simple (JSX) content
- class based: good for just about everything else (including event handling)
  - easier code organization
  - can use ```state``` means easier to handle user input
  - understands lifecycle events, means easier to do things when the app first starts

### R2D6 - July 25th, 2019
#### metasfresh webui frontend with ReactJS
- further digging into the metasfresh webui frontend code
- getting a better understanding about how things work after my first week of ReactJS learning
- decided to start the developer documentation of metasfresh webui frontend as part of my learning time, I'm thinking about using JSDocs or Gatsby for this

#### ReactJS: metasfresh webui with Storybook
- read about Storybook and how is can help developing encapsulated and reusable components
- wrote a story for a small component in metasfresh webui project and tested different configurations in isolation
- the styling is not compoinent based in metasfresh, so the component is not looking good in Storybook runner. I will see how to change this.

### R2D7 - July 26th, 2019
#### new ReactJS Challenge project: seasons
- created a new ReactJS challenge project to learn more about class based components, state and event handling
- adding sematic ui to the project

#### Using Geolocation API
- checked out and used the Geolocation API which is included in most browsers
- documentation can be found here https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API

### R2D8 - July 27th, 2019
#### Refactoring function based to class based component
- Rules of class base components
  - must be a javascript class
  - must extend subclass React.Component
  -  muste define a ```render``` method that returns some amount of jsx

#### State in React Components
- Rules of State
  - only usable with class components (can be used with functional components using the ```hooks``` system)
  - don't confuse props with state
  - ```State``` is a javascipt object that contains data relevant to a component
  - updating ```state``` on a component causes the component to (almost) instantly rerender
  - ```State``` must be initialized when a component is created
  - Never do direct assignment to state (besides initialization), always use setState 
  - don't use heavy calculations in render method (is called a lot and shall remain performant)

#### Conditional rendering in React
- using if statements in render() method to decide what content shall be returned

#### React component lifecycle
- Lifecycle methods are functions that are called discrete or distinct during the lifecycle time
    - constructor 
        - optional
        - defined and called when new component is created
        - good place to do one-time setup e.g. state initialization
        - for cleaner code, it is not recommended to add data loading to the constructor method. leave this for componentDidMount method
    - render 
        - not optional
        - content is now visible on screen
        - important: avoid doing anything besides returning JSX
    - componentDidMount 
        - optional
        - is called immediatly after a component shows up first time on the screen/ browser
        - good place to do data loading
    - componentDidUpdate
        - optional
        - is called automatically every time our component is updated
        - every time the render method is called, the jsx will be returned and componentDidUpdate will be invoked
        - good place to do data loading when state/ props change
    - componentWillUnmount
        - optional
        - is called automatically as soon a component will be vanished
        - cleanup of a component
        - good place to do cleanup (especially for non-React stuff)
    - Further livecycle methods exist but are very rarely used
        - shouldComponentUpdate
        - getDerivedStateFromProps
        - getSnapshotBeforeUpdate

#### Avoid the constructor-super-props-state ceremony?
The constructor part of a React Component
```js
class App extends React.Component {
    constructor(props) {
      super(props);
      this.state = {lat: null, errorMessage: ''};
    }
```
can be substituded easily with an instance property
```js
class App extends React.Component {
    state = {lat: null, errorMessage: ''};
```
Babeljs will take care about generating the right code for the constructor and super(props).

#### Passing state as props
- passing a state property as prop to a sub component
- when state property changes then the component is rerendered and also the sub component is rerendered automatically

#### Using component css
- import css file in component using ```import 'Component.css';```
- webpack takes this information and includes the css into the index.html file

#### React component defaultProps
- using ```ComponentName.defaultProps``` object to declare default props in case the component properties were not set when instanciating

#### Avoiding conditionals in render method
- don't use conditionals in render method
- use a helper method instead (e.g. renderContent())
- this makes it easier to maintain the the JSX layout/ structure that's returned

### R2D9 - July 28th, 2019
#### ReactJS coding challenges
- refactored a function-based to a class-based component
- created a Clock component that shows the time in seconds with componentDidMount, interval and state change with rerender 

#### New pics project
- created a new react app called pics
- creating a multi component structure with components folder in src folder

### R2D10 - July 29th, 2019
#### Learning and coding ReactJS
- new SearchBar component for my project
- added sematic UI CSS to my project and did some styling with it
- added an event Handler to SearchBar component with onChange event
  - onChange: user changes text in an input
  - onClick: user clicks on something
  - onSubmit: user submits a form
- community convention for event handling methods
  - on (prefix)
  - Input (tagname)
  - Change (eventname)

### R2D11 - July 30th, 2019
#### Debugging & Fixing metasfresh
- debugged metasfresh WebUI and found out why the Webcam usage was failing in newer Browser versions
- Reason was a deprecated method that was used in the Image component
- fixed and tested 
