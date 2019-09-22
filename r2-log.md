# 100DaysOfCode Log - Round 2 - Mark Krake (@metas-mk)

The log of my 2nd Round of #100DaysOfCode challenge. Started on [July 19, Friday, 2019].

## Log

In my first life I was a COBOl and Mainframe Software Developer. Being a Product Owner and Requirements engineer in the last decade, I did not code anymore and found out that I was missing it like hell. I made a plan to get back into coding frequently and am now on a mission learning JavaScript and ReactJS. I started my personal #100DaysOfCode challenge on March 24th 2019 but only logged my daily progress via Twitter (@markkrake). I'm starting the 2nd round an will log my progress here.

### R2D0 - July 19th, 2019

- Setup my git repository to log my 2nd round progress of my #100DaysOfCode challenge

### R2D1 - July 20th, 2019

#### How to Setup ESLint for my project in VSCode?

- `cd` into your `coding-repository`
- `npm init -y`
- `npm install -D eslint eslint-config-standard eslint-plugin-import eslint-plugin-node eslint-plugin-promise eslint-plugin-standard`
- create `.estlintrc.js` with ```module.exports = {"extends":"standard"};
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
- `npm install --save faker`

#### Having issues starting local webserver

- After install of Faker.js the local websever did not want to start anymore. I deleted the node_modules folder of my project and did a fresh `npm install`. After that used `npm start` to try again, and worked.

### R2D3 - July 22nd, 2019

#### new git command

- first time used `git commit --amend`
  - allows you to adjust the last commit message directly via editor

#### Deduplicating JSX content, component nesting

- refactoring JSX content and extracting to an own component `CommentDetails.js`
- coding convention: Components are written with UpperCamelCase
- joined component with main App via `export default` and `import`
- using the component as JSX tag `` in render method of the main App

#### Props in a nutshell: Using react props system

- component hierarchy, parent component, child components or children
- props = properties
- props: system for passing data from a parent component to a child component
  - goal is to customize or configure a child component
  - provide information from parent to child (via JSX property) e.g. `<CommentDetails date="Today 6:05PM" />`
  - consume infomation in child (via props argument object) e.g. `{props.date}`

### R2D4 - July 23rd, 2019

#### What is props validation?

- Runtime type checking for React props and similar objects.
- during debugging of metasfresh-webui-frontend I came past an eslint warning `... is missing in props validation`
  - documentation here https://www.npmjs.com/package/prop-types

#### Component Reuse ReactJS

- component nesting: a component can be shown inside of another
- component reusability: components shall be easily reusable through out an application
- component configuration: a component shall be configurable when it's created

#### Nesting components & props.children

- wrapped the comments component into an approval component via jsx
- used `props.children` to consume the nested component

### R2D5 - July 24th, 2019

#### Function based vs. class based components

- function based: good for simple (JSX) content
- class based: good for just about everything else (including event handling)
  - easier code organization
  - can use `state` means easier to handle user input
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
  - muste define a `render` method that returns some amount of jsx

#### State in React Components

- Rules of State
  - only usable with class components (can be used with functional components using the `hooks` system)
  - don't confuse props with state
  - `State` is a javascipt object that contains data relevant to a component
  - updating `state` on a component causes the component to (almost) instantly rerender
  - `State` must be initialized when a component is created
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

- import css file in component using `import 'Component.css';`
- webpack takes this information and includes the css into the index.html file

#### React component defaultProps

- using `ComponentName.defaultProps` object to declare default props in case the component properties were not set when instanciating

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

### R2D12 - July 31th, 2019

#### Diving into JSDoc

- Reading into JSDoc, starting to do the setup for metasfresh WebUI project

#### Code coverage with Cypress

- Watching a webcast about howto reach code coverage with cypress testing

### R2D13 - August 1st, 2019

#### Learning ReactJS

- learned an alternate way of adding an event handler to an onChange event

```js
// Approach with callback function reference
onChange={this.onInputChange}
```

```js
// Alternate approach for oneline functions with arrow function
onChange={e => console.log(e.target.value)}
```

#### Controlled vs. uncontrolled components example

- controlled
  - user types input
  - callback gets invoked
  - we call setState with the new value
  - component rerenders
  - input is told what value it has (coming from state)

```js
value={this.state.term}
onChange={e => this.setState({ term: e.target.value })}
```

- uncontrolled
  - to know the value one has to get it from input dom element

### R2D14 - August 2nd, 2019

#### Prevent default browser logic for HTML Form

- after pressing `return` or `enter` in an HTML for, we don't want the page to be refreshed automatically. We ofren want to prevent the browser from doing to. This can be done with overwriting the onSubmit event.

```js
...
  onFormSubmit(event) {
    event.preventDefault();
  }
...
render() {
    return (
      <div className="ui segment">
        <form onSubmit={this.onFormSubmit} className="ui form">
```

#### Understanding 'this' in JavaScript

- had a weird error today `TypeError: Cannot read property 'term' of undefined`
- happened with the following code

```js
  onFormSubmit(event) {
    event.preventDefault();
    console.log(this.state.term);
  }
   render() {
    return (
      <div className="ui segment">
        <form onSubmit={this.onFormSubmit} className="ui form">
...
```

- roughly: this is initially bound to the object left of the dot to the method/ function call
- some solutions to solve the case

```js
  constructor() {
    super();
    this.onFormSubmit = this.onFormSubmit.bind(this);
  }
```

- alternatively can be solved in using ES6 arrwow function instead.

```js
onFormSubmit = event => {
  event.preventDefault();
  console.log(this.state.term);
};
```

### R2D15 - August 3rd, 2019

#### VSCode: How to use emmet in JSX

```json
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
```

#### Communicating child to parent

- Invoking callbacks in children
  - pass callback function reference in parent via prop in child component JSX
  - in callback function of child then pass the state as argument to the referenced callback function via props

_Parent component_

```js
class App extends React.Component {
  onSearchSubmit(term) {
    console.log(term);
  }

  render() {
    return (
      <div className="ui container" style={{ marginTop: '10px' }}>
        <SearchBar onSubmit={this.onSearchSubmit} />
```

_Child component_

```js
// child
onFormSubmit = event => {
  event.preventDefault();

  // prop is the reference to callback function of App.onSearchSubmit()
  this.props.onSubmit(this.state.term);
};
```

#### Making API Requests with ReactJS

- install axios via npm `npm install --save axios`
- Sidenote: import statements from 3rd party providers shall be above the import statements of your own App
- Developer API Key from [unsplash.com](https://unsplash.com/developers)
  - API root is `https://api.unsplash.com/`
  - Authentication `Authorization: Client-ID YOUR_ACCESS_KEY`
  - Endpoint for search photos `/search/photos`
  - params object added
  - headers object added for Authorization
- axios.get() is an asynch function. The result is a promise. The promise can call a callback function as soon the response has arrived.

```js
// promise ... then
axios.get(...).then(() => {...});
```

- alternative with async ... await (preferred)

```js
async onSearchSubmit(term) {
    // async ... await (preferred)
    const response = await axios.get(...);
```

### R2D16 - August 4th, 2019

#### Setting state after async requests

- ran into the 'this' binding issue again. this time with an async funtion.
- adjusted the function to an ES6 arrow funtion solved the issue

```js
onSearchSubmit = async term => {
  // promise
  const response = await axios.get('https://api.unsplash.com/search/photos', {...}
    ...
  });
  this.setState({ images: response.data.results });
};
```

#### Axios: Extracted baseURL and headers into own file

- created an own js file and folder structure to avoid having the API key and baseURL in Application component itself
- added the folder to .gitignore to avoid commiting to public repository

#### Rendering Lists with map

- Pics project: Using array map to iterate over API response
  - created a new ImageList component
  - used array map to iterate over the API response and give out the images as image tag
  - currently there is a warning in console 'Each child in ... an array or iterator should have a unique "key" prop. Will take care about that next.

### R2D17 - August 5th, 2019

#### Adding a key to list component

- to allow React to find the needed list elements to rerender in a more efficient way, it is needed to add a key property to the list component root element that is returned

```js
return <img key={image.id} src={image.urls.regular} alt="images" />;
```

- adding a key prop also eliminates the warning `'Each child in ... an array or iterator should have a unique "key" prop`
- adding an image alt property for a11y, filled with image.description from unsplash API response

### R2D18 - August 7th, 2019

#### Styling the pics search results

- adding some styling to the pics search result
- included a css for ImageList component
- adding grid style for image results
- using grid-auto-rows to define the height of rows in grid styling
- new ImageCard component. This shall allow to create individual styles per Image for grid style
  - let the ImageCard render itself and its image
    reach into the DOM and figure out the height of the image (via ReactRefs)
  - set the image height on state to get the component to rerender
  - when rerendering, assign a 'grid-row-end' to make sure the image takes up the appropriate space

#### Sidenotes

- only add to state when it's expected that the content will change over time, e.g. it does not make sense to add the property image-height to state for a given image.

#### React Refs

- gives access to an single DOM element. in vanilla JS the equivalent is `document.querySeletor()`
- we create refs in the constructor, assign them to instance variables, then pass to a particular JSX element as props

```js
constructor(props) {
    super(props);

    this.ImageRef = React.createRef();
  }
```

### R2D19 - August 8th, 2019

#### Accessing the image height

- when trying to access the image height in componentDidMount() via React.createRef().current.clientHeight it shows 0. What's happening?
  - the component is loaded, but the browser has not downloaded the image yet
  - when checking the console.log of that image ref element it shows the clientHeight although. This happens because the browser is fancy and shows the infomraiton as one opens the object tree.
- added an event listener in componentDidLoad() that is triggered after the image is loaded.

```js
componentDidMount() {
    this.ImageRef.current.addEventListener('load', this.setSpans);
  }
```

#### Same key/ value pair

- when having identical key value pair in objects then it can be shortened since ES2015

```js
// until ES2015
this.setState({ spans: spans });

// since ES2015
this.setState({ spans });
```

### R2D20 - August 9th, 2019

#### Starting Youtube video search project

- This project shall allow to search videos using the free youtube API. The app shall have a search bar, a video player and a list of videos that match the search criteria. The search results can be selected and then the video is started. The app shall be built with ReactJS. The following component hierarchy is planned:
  - App
    - Searchbar
    - Video Detail
    - Video List
      - Video Item

### R2D21 - August 10th, 2019

#### New Component SearchBar

- Created a new class based SearchBar component
  - imported React (for JSX)
  - added render method, return JSX
  - added export statement
- Import SearchBar in App component
  - added SearchBar component to JSX render method

#### Semantic UI

- included [semantic ui CSS](https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css) to index.html
  - Styling in SearchBar component
    - using `className="ui segment`, this draws a rectangle
    - using `ui form`, `field`
  - Syling in App component
    - using `ui container`, adds a margin left/ right of the SearchBar component

#### SearchBar improvements

- turning SearchBar from an uncontrolled to controlled component
  - storing the search term content in state instead of html form input element
  - overriding the default browser behavior of form on enter
    `event.preventDefault();`

### R2D22 - August 11th, 2019

#### Integrating the Youtube API

- Integrated the Youtube API
- Using Axios to send requests and receive responses
- created a new API Key at https://console.developers.google.com
- created a new folder src/apis and added a new file called `youtube.js` there. This file keeps the API Key as variable.

```js
const KEY = '<api-key>';
```

- added the src/apis folder to .gitignore
- visited https://developers.google.com/youtube/v3/docs/search/list to find out how to use the youtube data api
  - Request: `GET https://www.googleapis.com/youtube/v3/search`
  - Parameters:
    - part: 'snippet' (will show name, description of viedo)
    - q: 'searchquery'
    - maxResults: 5

```js
export default axios.create({
  baseURL: 'https://www.googleapis.com/youtube/v3',
  params: {
    part: 'snippet',
    maxResults: 5,
    key: KEY
  }
});
```

#### New Component VideoList

- new functional component VideoList
- adding new component VideoList to App render method
- passing App state as props to VideoList
- in VideoList destructuring props directly to ({videos})

#### New Component VideoItem

- new functional component VideoItem
- creating mapp in VideoList and returning a VideoItem for each entry
- adding video title from youtube API response
- adding video thumbnails from youtube API response
- adding some styling to VideoList and Video item with SemanticUI

### R2D23 - August 12th, 2019

#### Communication from child to parent in ReactJS

For the video player I want to select a VideoItem element. This shall show the seleted Video in the new VideoDetail component. How shall this be done?

- App:
  - state `selectedVideo: video`
  - props `videos: [videos, ...]`
  - props `onVideoSelect: () => ()`
- VideoList
  - props `video: video`
  - props `onVideoSelect: () => ()`
- VideoItem

Create a new method in App component and pass a reference to that method down to VideoList. Further pass the reference down to VideoItem. Any time the user clicks a VideoItem we tell VideoItem to call the callback function `onVideoSelect`. When it calls the callback it passes in the video that was selected. This way it invokes a method in the App component with the video that was clicked on.

When communicating from parent to child, this is done via the props system. When communicating from child to parent this is done via callback functions.

#### Styling the VideoDetails component

- retrieved the video description via youtube API and added some SemanticUI style to the VideoDetails component
  - surrounding div tag with `ui segment`
  - div tag header with `ui header`
  - paragraph that takes the `{video.snippet.description}`

#### Adding a video player to VideoDetails

- added an iframe tag in VideoDetails component
- surrounded by div tag with `ui embed` style (SemanticUI will take care about the styling)
- how to embed a youtube video?
  - Check out youtube. Press share button on any video. Press embed. It shows an iframe example. You can see how the url is built with video identifier and video of in it. This is what is needed for the embedded video url that shall be built.
- getting rid of some warnings
  - adding a title to VideoDetail iframe
  - adding an alt prop to the img tage in VideoItem
  - adding a key prop to VideoList div tag
- adding SemanticUI grid style for VideoDetail (11 columns) and VideoList (5 columns) component
- defaulting the video selection in VideoDetail
  - in onTermSubmit() so that the first video result is shown in VideoDetail
  - componentDidMount() calls the onTermSubmit with default search term

### R2D24 - August 13th, 2019

#### Starting with Redux

- What is Redux?
  - State management library
  - Makes creating complex applications easier
  - Not required to create a React app!
  - Not explicitly designed to work with React

#### Redux Cycle

- Action Creator (analogy to insurance company: customer dropping off the form)
  - a function that will return a plain javascript object
- Action (analogy to the form that is transmitted to the insurance company)
  - the plain javascript object that was created by the Action creator
  - has a type property (describes some change that we want to make in our data)
  - has a payload property (describes some context about the change that we want to make)
  - purpose to describe some change to the data of our apllication
- dispatch (analogy to the form receiver at the insurance company that copies the form and forwards it to each department in the insurance company, together with selected relevant data)
  - the dispatch function takes in an action and makes a copy of the action object and pass it off to a bunch of different places inside of our application
- Reducers (analogy to each department in the insurance company)
  - a reducer is a function that takes in a action and some amount of existing data
  - it is going to process that action and make some change to that data and return it to be centralized in some other location
- State (analogy to the compiled department data)
  - a central repository of all information that has been created by our reducers
  - with this our application can easily reach into the central repository to achieve needed infomration and does not have to ask every 'Department' to get the information

#### Redux Example in Codepen

`Example for action creators and actions`

- by convention the action type is written in upeprcase with underscore

```js
// People dropping off a form (Action creator)
const createPolicy = (name, amount) => {
  return {
    // Action (a form in our analogy)
    type: 'CREATE_POLICY',
    payload: {
      name: name,
      amount: amount
    }
  };
};

const deletePolicy = name => {
  return {
    type: 'DELETE_POLICY',
    payload: {
      name: name
    }
  };
};

const createClaim = (name, amountOfMoneyToCollect) => {
  return {
    type: 'CREATE_CLAIM',
    payload: {
      name: name,
      amountOfMoneyToCollect: amountOfMoneyToCollect
    }
  };
};
```

`Example of dispatch`

- is part of the Redux Library itself
- each dispatch runs a whole Redux cycle (see Resumee of Redux Cycle)

```js
// wire up all our Reducer functions is done via combineReducers
const { createStore, combineReducers } = Redux;

const ourDepartments = combineReducers({
  accounting: accounting,
  claimsHistory: claimsHistory,
  policies: policies
});
```

```js
const store = createStore(ourDepartments);

store.dispatch(createPolicy('Alex', 30));
store.dispatch(createPolicy('Jim', 40));
store.dispatch(createPolicy('Bob', 50));

store.dispatch(createClaim('Alex', 120));

store.dispatch(deletePolicy('Bob'));

console.log(store.getState());
```

`Example of reducer`

- always return a new dataset. never ever modify the old dataset and return that.

```js
// claimsHistory Department
// oldListOfClaims default to empty array
const claimsHistory = (oldListOfClaims = [], action) => {
  if (action.type === 'CREATE_CLAIM') {
    // we care about this action (form!)
    return [...oldListOfClaims, action.payload];
  }

  // we don't care about this action (form!)
  return oldListOfClaims;
};
```

```js
// accounting Department
// bagOfMoney default to 100
const accounting = (bagOfMoney = 100, action) => {
  if (action.type === 'CREATE_CLAIM') {
    return bagOfMoney - action.payload.amountOfMoneyToCollect;
  } else if (action.type === 'CREATE_POLICY') {
    return bagOfMoney + action.payload.amount;
  }

  return bagOfMoney;
};
```

```js
// policies Department
const policies = (listOfPolicies = [], action) => {
  if (action.type === 'CREATE_POLICY') {
    return [...listOfPolicies, action.payload.name];
  } else if (action.type === 'DELETE_POLICY') {
    return listOfPolicies.filter(name => name !== action.payload.name);
  }

  return listOfPolicies;
};
```

#### Resumee of Redux Cycle

- to change the state of our app we call an Action Creator
- the Action Creator produces an Action Object. The Action Object describes exactly how we want to change data in our Application,
- the Action gets fed to dispatch function which in terms creates copies of the Action Object
- the dispatch forwards the Action Object copies to each of the different Reducers
- the Reducers process those Actions, modify and return the new data. The returned data gets formed into a new State
- the State waits until we need to update again

The only way the state object can be updated is via the dispatch function in combination with Action creators and actions. There is now other way to reach into and update the state object under Redux.

#### New songs Project ReactJS & Redux

- created a new project via `create-react-app songs`
- deleted everything from the src folder
- created a new public github repository https://github.com/metas-mk/songs
- joined my local git repo with the new github repo via `git remote add origin <remote repository URL>`
- created a new functional App component. Class based components are mostly only needed if state is needed. With the use of Redux the need of class based components will be reduced.
- added SemanticUI to the project as stylesheet
- the songs project will have 2 components
  - SongList
    - shall display the list of song objects
  - SongDetail
    - shall display the title and the length of the given songs

#### How to setup Redux with React?

- React: Same lib I have been using all the time
- React-Redux: A bunch of helper functions to get React and Redux work nicely together.
- Redux: Redux lib

The environment can be stup in the project folder via `npm install --save redux react-redux`.

#### Project Setup with/ without Redux

`Without Redux`

- App stores
  - List of songs
  - Selected song
- App passes to Son List
  - List of Songs
  - onSongSelect callback
- App passes to SongDetail
  - selected song

`With Redux`

- App, SongList, SongDetail components passing very little information inbetween each other
- Reducers (only pieces of state in this App)
  - Song list reducer
  - Selected song reducer
- Action creators (only creator of state change)
  - select song

#### How is Redux integrated into the App?

- 2 new components, both created by React-Redux, we use instances of them and pass props to them
  - Provider (has the store/ state as props) and is redered first (even before App). The Provider has the reference to store.
  - Connect. The components that need access to the store will be wrapped into an instance of the Connect component. The connect component communicates with the Provider through the context system.
- React-Redux project structure
  - /src
    - /actions (contains files related to action creators)
    - /components (files related to components)
    - /reducers (files related to reducers)
    - index.js (sets up both the react and redux sides of the app)

### R2D25 - August 14th, 2019

#### Adding Action creator and reducers to the songs app

- New folder src/actions and new file index.js (webpack will identify index.ja as default when importing the folder)
- New folder src/reducer and new file index.js with the reducers SongReducer and SelectedSongReducer. Further added the combineReducers() function in there

`Wire up the Provider`

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import { createStore } from 'redux';
import App from './components/App';
import reducers from './reducers';

ReactDOM.render(
  <Provider store={createStore(reducers)}>
    <App />
  </Provider>,
  document.querySelector('#root')
);
```

Now all Components in our App can make use of the redux store with help of the Connect function.

In Component the connect function is called.

```js
export default connect()(SongList);
```

The connect function returns a function. This function is then invoked with the property of SongList component.

In component a new function `mapStateToProps` is implemented. This function is the configuration for the connect function/ component. The function is added to connect as prop.

```js
// state is the complete state of our Redux store
// mapStateToProps is naming convention
const mapStateToProps = state => {
  console.log(state);
  return state;
};

export default connect(mapStateToProps)(SongList);
```

#### IMPORTANT! Resumee of Redux in component integration

1. Import connect from react-redux

```js
import { connect } from 'react-redux';
```

2. Call connect and pass in the component as second function call prop, here SOngList

```js
export default connect(mapStateToProps)(SongList);
```

3. Define `mapStateToProps` function which always has a first argument of `state` (Redux store) and always returns an object which is going to show up as props inside the component. This object has also a reference to the dispatch method.

```js
// state is the complete state of our Redux store
// mapStateToProps is naming convention
const mapStateToProps = state => {
  return { songs: state.songs };
};
```

4. Calling Action creators from components. The Action creator is added to the connect function as second argument. The connect function adds the ActionCreator to the props of the component. This is the only way Redux knows that the function is an Action creator that can be forwarded to dispatch.

```js
import { selectSong } from '../actions';
...
export default connect(
  mapStateToProps,
  { selectSong }
)(SongList);
```

### R2D26 - August 15th, 2019

#### Debugging and bug fixing

- Debugged my song app. The selected song was not triggered after creating and wiring up the Action creator and reducer.
- Found the Bug. Was a trivial typo in the `selectedSongReducer()`

#### New SongDetail Component for the song App

- created the new functional based component `SongDetail()`

```js
import React from 'react';
import { connect } from 'react-redux';

const SongDetail = ({ song }) => {
  if (!song) {
    return <div>Select a song</div>;
  }
  return (
    <div>
      <h3>Details for:</h3>
      <p>
        Title: {song.title}
        <br />
        Duration: {song.duration}
      </p>
    </div>
  );
};

const mapStateToProps = state => {
  return { song: state.selectedSong };
};

export default connect(mapStateToProps)(SongDetail);
```

- imported the new component in `App.js` and created a JSX Tag for it to be rendered

### R2D27 - August 16th, 2019

#### Further Redux practice & Redux Thunk

- started a new ReactJS & Redux App `blog`
- it will receive data from https://jsonplaceholder.typicode.com/ and show a list of blog posts with author information
- installed a few additional libraries. new this time is `redux-thunk`
  - redux: the Redux library
  - react-redux: integration layer between React and Redux
  - axios: helps to make network requests
  - redux-thunk: middleware to make requests in a redux application

```
npm install --save redux react-redux axios redux-thunk
```

#### Tip for initial redux dummy reducer

If you quickly want to start a React-Redux project and don't want to start working on reducers yet, than you can just create a dummy reducer spo that your are not stalled by redux errors.

```js
import { combineReducers } from 'redux';

export default combineReducers({
  replaceMe: () => '666'
});
```

#### General Data loading with Redux

- Components are generalle responsible for fetching data they need by calling an action creator
  - Component gets rendered onto the screen
  - Component's `componentDidMount` lifecycle method gets called
    - for such cases a classbased component is needed to have access to the lifecycle methods
  - We call an action creator from `componentDidMount`
- Action creators are responsible for making API requests (this is where Redux-Thunk comes into play)
  - Action creator runs code to make an API request
    - the Action creator initiates the API request, the request can be done via another class or function
    - will use axios to do that
  - API responds with data
  - Action creator returns an `action` with the fetched data on the `payload` property
- We get fetched data into a component by generating new state in our redux store, then getting that into our component through mapStateToProps
  - Some reducer sees the action, returns the data of the `payload`
  - Because we generated some new state object, redux/ react-redux cause our React app to be rerendered

### R2D28 - August 17th, 2019

#### Further Redux practice & Redux Thunk

- App.js main component (functional based)
- First step fake reducer `src/reducers/index.js`

```js
import { combineReducers } from 'redux';

export default combineReducers({
  replaceMe: () => '666'
});
```

- Action creator `src/actions/index.js`

```js
export const fetchPosts = () => {
  return {
    type: 'FETCH_POSTS'
  };
};
```

- PostList.js component (class based)
  - import `connect from`react-redux`
  - componentDidMount() Action creator call fetchPosts()

```js
componentDidMount() {
  this.props.fetchPosts();
}
...
export default connect(
  null,
  { fetchPosts }
)(PostList);
```

- new jsonPlaceholder

```js
import axios from 'axios';

export default axios.create({
  baseURL: 'https://jsonplaceholder.typicode.com'
});
```

- Modified Action creator index.js for fetchPosts()
  - This is Bad code and not allowed in Redux!!! Action creators must return plain objects.
  - Leads to error `Error: Actions must be plain objects. Use custom middleware for async actions.`

```js
import jsonPlaceholder from '../apis/jsonPlaceholder';

export const fetchPosts = async () => {
  // Bad!!! cannot be done like this.
  // Action creators must return plain objects
  const response = await jsonPlaceholder.get('/posts');
  return {
    type: 'FETCH_POSTS',
    payload: response
  };
};
```

#### Understanding Async Action Creators

- What's wrong with 'fetchPosts'?
  - Action creators must return plain JS objects with a type property - fetchPosts is not.
  - By the time our action gets to a reducer, we won't have fetched our data!
- But the code in Action cretor looks like a plain object! No. Trying the Action creator in https://babeljs.io shows to what the code is transpiledm and thats not a plain JS object. All because of the async/ await.
- What happens behind the scenes?
  - componentDidMount() calls this.props.fetchPosts().
  - Then Redux dispatches the Action creator and invokes fetchPosts().
  - The transpiles Action creator, because of async/ await returns via case 0 the request.
  - That's why we don't receive a plain object but the request `jsonPlaceholder.get('/posts')` instead
  - only in a further case 2 the expected plain JS Object is returned
  - without async/ await the transpiled code works, but we don't receive data directly, we receive a promise to receive data some time in the future. It can happen that we don't have the data already at the time the reducer is run!
    - Action creator called
    - Action returned
    - Action dispatched
    - Reducer run
    - All above happens in fractions of a ms. The data return from an async call takes much longer.

### R2D29 - August 18th, 2019

#### Syncronous action vs. Asyncrononus action creator

- Syncronous action creator: instantly returns an action object with data ready to be directly processed by reducers
- Asyncronous action creator: takes some amount of time for it to get its data ready to be consumed. Happens for example with network requests. To deal with thode in Redux we always have to use a middleware (e.g. Redux Thunk)

#### Where does middleware locate in the Redux cycle and what is it?

- middleware is located between dispatch and reducers
  - dispatch forwards the actions to the middleware
  - middleware does whatever it shall do with the actions and sends it to the Reducers to be consumed
- middleware is a plain JS function that gets called with every action we dispatch
  - has the ability to stop or modify actions
  - middleware is most popular for dealing with async actions (e.g. Redux Thunk) but also others exist (e.g. middleware to console log dispatches)

#### Details of Redux Thunk

- Normal Redux Rules
  - Action creators must return actions which are plain JS objects
  - Actions must have a type property
  - Actions optionally have a payload
- Rules with Redux Thunk
  - Action crators can return action objects or return functions
  - when returning an action object it must have a type
  - when returning an action object it can have a payload

#### Partial Redux cycle with Redux Thunk

Redux-Thunk source code can be found at https://github.com/reduxjs/redux-thunk

- Action creator is called and creates an object or a function
- `Action` is passed into the dispatch function
- dispatch sends the `Action` to the middleware Redux Thunk
  - inside of Redux Think middleware it decides if plain JS object is received or a function
    - plain JS objects are passed along to all Reducers directly
    - functions are invoked by Redux Thunk and dispatch and getState functions are added as arguments.
    - the function is invoked with dispatch and waited until the request is finished
    - after request is complete the dispatch action happens manually
    - a new action object is created and dispatched via the dispatch function

#### How to hook up a middleware to Redux store (here Thunk)

In root index.js just add a few imports and arguments to createStore()

```js
...
import { createStore, applyMiddleware } from 'redux';
...
import thunk from 'redux-thunk';

const store = createStore(reducers, applyMiddleware(thunk));

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.querySelector('#root')
);
```

### R2D30 - August 19th, 2019

#### Rules of Reducers

- a reducer must return any value besides `undefined`. returning `undefined` leads to an error message.
- are pure
  - produces `state`, or data to be used inside of the app by using the initial data received from state and the action object that has been dispatched
    - when starting the Redux application each reducer is automatically run one time to produce the default state value
    - it receives two values.
      - undefined (is then initialized by the reducer default argument value)
      - some action object
    - each other time the reducer runs it receives the current state as first argument and a changed action object.
  - must not reach outside itself in order to decide what value to return. it's only using the previos state and action object to produce the return value.
- shall not manipulate its props/ argument `state`
  - is a convention. Redux will not throw any errors if one does.
  - but Redux will not let React know that a change was done and therfor the components will not be rerendered

Check out combineReducers Code from the Redux project https://github.com/reduxjs/redux/blob/master/src/combineReducers.js

```js
...
let hasChanged = false
    const nextState = {}
    for (let i = 0; i < finalReducerKeys.length; i++) {
      const key = finalReducerKeys[i]
      const reducer = finalReducers[key]
      const previousStateForKey = state[key]
      const nextStateForKey = reducer(previousStateForKey, action)
      if (typeof nextStateForKey === 'undefined') {
        const errorMessage = getUndefinedStateErrorMessage(key, action)
        throw new Error(errorMessage)
      }
      nextState[key] = nextStateForKey
      hasChanged = hasChanged || nextStateForKey !== previousStateForKey
    }
    hasChanged =
      hasChanged || finalReducerKeys.length !== Object.keys(state).length
    return hasChanged ? nextState : state
  }
...
```

#### Lodash - a JavaScript utility library

Lodash is a nice library that provides a lot of functions that help in JavaScript Development. It can be found here: https://lodash.com/docs/4.17.15
Just open the console on documentation page and you can try it out directly.

#### Fetching user data for each post

The user data can be fetched via `/users` endpoint. Routes are provided to only fetch user data for a given id.

What shall be done in the app?

- Fetch posts
- Show posts in PostList
- Each element in PostList shows the UserHeader
- User Header is given ID of user to show
- Each UserHeader attempts to fetch its user
- Show users in each UserHeader

### R2D31 - August 21st, 2019

#### JSDoc

- Reading about how to get started with [JSDoc](https://jsdoc.app/)
- Evalutating if it can be used for the open source ReactJS project [metasfresh](https://github.com/metasfresh/metasfresh-webui-frontend)
- Opened a development branch in the repository and installed JSDoc locally `npm install --save-dev jsdoc`
- Created the first docs with `.\node_modules\.bin\jsdoc .\src\ -r`
- The result can be found in the default folder `.\out`

### R2D32 - August 22nd, 2019

#### JSDoc

- Adding a dependancy to `package.json`

```js
...
"scripts": {
  "docs": "./node_modules/.bin/jsdoc "
}
```

- Adds a configuration file for JSDoc and adding a parm to the dependancy to use the config file. The document creation can now be done via `npm run docs`.

_package.json_

```js
"scripts": {
    ...
    "docs": "./node_modules/.bin/jsdoc -c jsdoc.json",
    ...
  }
```

_jsdoc.json_

```js
{
  "source": {
    "include": ["./src"],
    "includePattern": ".js$",
    "excludePattern": "(node_modules/|docs)"
  },
  "plugins": ["plugins/markdown"],
  "opts": {
    "encoding": "utf8",
    "readme": "./readme.md",
    "destination": "docs/",
    "recurse": true,
    "verbose": true
  }
}
```

- Added an example Tutorial section to the generated JSDoc
  - New folder `Tutorials` with an example file `example-tutorial.md`. Added an option to the `jsdoc.json`

```js
  "opts": {
...
    "tutorials": "./tutorials"
```

- Per default the tutorial title is shown with the filename. To change that you can create a `totorial.json` file in the tutorials folder and do a filename title assignment.

```js
{
  "example-tutorial": {
    "title": "Example Tutorial"
  }
}
```

- Installed the JSDoc theme `better-docs` locally and saved dependancy `npm install --save-dev better-docs`
  - After install added the template option to jsdoc.json

```js
  "opts": {
    ...,
    "template": "./node_modules/better-docs/"
  }
```

- Added category support to JSDocs. Now the `@category` annotation can be used to add the comment into a category.

```js
{
  ...,
  "plugins": ["plugins/markdown", "node_modules/better-docs/category"],
  ...
  }
}
```

### R2D33 - August 23rd, 2019

#### JSDoc

- I dived into the sourcecode of [metasfresh-webui-frontend](https://github.com/metasfresh/metasfresh-webui-frontend) and started documenting the component structure of the project.

- Found out how to document functional React components and their props. Here an example:

```js
/**
 * Separator for element groups
 * @param {object} props Component props
 * @param {string} props.title Separator title
 * @param {bool} props.collapsible Separator collapsible
 * @param {bool} props.sectionCollapsed Separator collapsed
 * @param {*} props.idx Index
 * @param {function} props.onClick Callback function for onClick Handler
 * @param {*} props.tabId Tab ID
 */
```

### R2D34 - August 24th, 2019

#### JSDoc

- Further examining I the ReactJS code of [metasfresh-webui-frontend](https://github.com/metasfresh/metasfresh-webui-frontend) and documenting the component structure of the project. Event though I'm not understanding everything in detail directly, documenting is a great way to learn step-by-step how the application works and helps other new peopls to the project to have a better prepared ressource to learn.

#### Further ReactJS/ Redux learning

- Working on my blog coding challenge project. Created a new action creator `fetchUser()`. This one fetches a user object for a given user id prop from jsonPlaceholder.

- Created a new reducer called usersReducer. Wired the new reducer up in `reducers/index.js` `combineReducers`.

- In UserHeader component created the mapStateToProps()

- Added the UserHeader into PostList component.

- Refactored mapStateToProps. Extracted logic from component to mapStateToProps method. The method takes another argument `ownProps` which is a reference to the component props.

- Any computation that shall be done on the Redux state, shall be done in the mapStateToProps method instead of component itself.

### R2D35 - August 25th, 2019

#### Blog Project, ReactJS/ Redux learning

After finishing the practice blog project it happens that each Instance of UserHeader makes a request to the API to receive the user data. This is not efficient. If a user is already know, the user data shall be reused and the additional requests shall be avoided.

- trying lodash to solve this, using the `memoize()` function. Trying this example in the browser console at https://lodash.com/docs/4.17.15#memoize

```js
// example
function getUser(id) {
  fetch(id);
  return 'Made a request!';
}
```

```js
getUser(5);
```

The console shows a log for each request made anf in the network tab (XHR) each time a request is shown. Now adding the lodash function `memoize()`

```js
const memoizedGetUser = _.memoize(getUser);
```

```js
memoizeGetUser(5);
```

Once the `memoizeGetUser()` is run with a given ID it does not create a request for the same ID again. The original function is not invoked anymore. It returns what was received previously with the identical set of arguments.

- Installed lodash with `npm install --save lodash`.

- refactored the action creator for fetchUser

```js
import _ from 'lodash';
...
export const fetchUser = id => dispatch => _fetchUser(id, dispatch);

// private function for memoizing action creator
const _fetchUser = _.memoize(async (id, dispatch) => {
  const response = await jsonPlaceholder.get(`/users/${id}`);

  dispatch({ type: 'FETCH_USER', payload: response.data });
});

```

The downside of this approach is that each User can only be fetched one time during a session. It can happen that User data changes an one will want to refetch the user data. This needs another solution.

The new apporach will be like this:

- New action creator fetchPostsAndUsers()
  - Call `fetchPosts`
  - Get a list of posts
  - Find all unique userId's from the list of posts
  - Iterate over the unique userId's
  - Call `fetchUser` with each userId

Refactored action creator. Still using a bit of lodash.

```js
export const fetchPostsAndUsers = () => async (dispatch, getState) => {
  await dispatch(fetchPosts());

  const userIds = _.uniq(_.map(getState().posts, 'userId'));
  userIds.forEach(id => dispatch(fetchUser(id)));
};
```

### R2D36 - August 26th, 2019

#### Documenting metasfresh frontend

- Reading into the metasfresh opensource erp frontend code based on ReactJS/ Redux
- Documenting Components with JSDoc

### R2D37 - August 27th, 2019

#### ReactJS props validation

- Reading about props validation. I'm thinking about introducing prop-types to each component in metasfresh frontent project to be able to know all props and their format via PropTypes. PropTypes checking is only done in development mode. For performance reasons the check is not triggered in production environment.
  -The official documentation about prop-types can be found here https://github.com/facebook/prop-types/blob/master/README.md
- The PropTypes can be installed as follows `npm install prop-types --save`
- PropTypes can be imported into project files as follows

```js
import PropTypes from 'prop-types';
```

Here an example how to uses the PropTypes in your component:

```js
ComponentName.propTypes = {
  // basic types
  anyProp: PropTypes.any,
  booleanProp: PropTypes.boolean,
  numberProp: PropTypes.number,
  stringProp: PropTypes.string,
  functionProp: PropTypes.function,
  symbolProp: PropTypes.symbol,
  arrayProp: PropTypes.array,
  objectProp: PropTypes.object,
  // renderable types
  nodeProp: PropTypes.node,
  elementProp: PropTypes.element,
  // instance types
  personProp: PropTypes.instanceOf(Person)
  // multiple types
  enumProp: PropTypes.oneOf([true, false, 0, 'Unnown'])
};
```

#### Documenting metasfresh frontend

- Proceeding with the developer documentation of the metasfresh-webui-frontend project.
- Creating PropTypes for component Modal.js

#### Wrap up of Redux Thunk practice project

- imported Redux Thunk
- wired up Thunk to Redux store via applyMiddleware(thunk) which is a function from the Redux library itself
- passed the result of that as 2nd argument to createStore()
- very time we apply an action it is sent to Thunk via Middleware
- after that the action will be sent to all of our action reducers
- the rules of our action creators changed so we can now not only return an object but also a function (outer function that returns an inner function)
- action creator that calls other action creators and then manually dispatches to reducer
- reducers with common switch syntax
- reducers always have to return a new array/ object so that Redux recognizes that we made a change to data and our component can be rerendered

#### New practice project similar to twitch.tv

- Open Boardcaster Software (OBS) streaming on PC
- Stream the desktop via Real time messaging protokoll (RTMP) server
- RTMP server broadcasts the feed to multiple viewers (viewer browser)
- web server that has a list of currently streamed videos
- selecting a video makes a request to RTMP server to receive the stream

### R2D38 - August 28th, 2019

#### metasfresh developer documentation

- Proceeding with the developer documentation of the metasfresh-webui-frontend project.
- Creating PropTypes for different components

#### Mockups for twitch.tv practice project

- Different pages/ screen. URL determines which content will be shown. Different components shown per page
- Login/ Logout auth system via google login
- Main Landing page with list of all different streams available, each shown with stream title and stream description underneath
- If user clicks a stream the user is taken to the video page and the stream is started
- User is not logged in
  - User can view a list of all streams/ channels
  - User can view video for a single stream
- User is logged in
  - User can create a new stream/ channel
  - User can edit a stream/ channel they have created
  - User can delete a stream/ channel they have created
- Once logged in, the main page is shown.
  - The title and description of streams can be edited.
  - Also deleting is possible.
  - Further new streams can be created.

#### React Router time

- installed React Router to my project with `npm install --save react-router-dom`
  - react-router-dom provides the navigation for dom based/ browser based application
  - react-router is the core navigation library (don't install this manually)
  - react-router-native is the navigation for react-native apps
  - react-router-redux is the binding between Redux and React Router (not needed)
- Import the needed components from 'react-router-dom'

```js
import { BrowserRouter, Route } from react-router-dom;
```

- add the routes to the components like this

```js
...
const PageOne = () => {
  return <div>PageOne</div>;
};

const PageTwo = () => {
  return <div>PageTwo</div>;
};

const App = () => {
  return (
    <BrowserRouter>
      <div>
        <Route path="/" exact component={PageOne} />
        <Route path="/pagetwo" exact component={PageTwo} />
      </div>
    </BrowserRouter>
  );
};
...
```

### R2D39 - August 29th, 2019

#### React Router time

- React Router only considers patterns after domainname and ports definition in the url (e.g. `metasfresh.com/window/143` only `/window/143` is checked by React router)
- the pattern is defined in the path prop for Route component
- inside a React route application one can have multiple route components that match a given url and all show themselves
  - this is a wanted functionality for nested components
- the keyword `exact` Route only considers exactly given path properties, so for `path="/" exact` only paths with only "/" is matched. If not using exact also paths like "/12345" will be matched. The function called is

```js
extractedPath.contains(path);
```

- with `exact` set, the rule is changed to

```js
extractedPath === path;
```

- How does a prop get interpreted which only has a keyword in JSX?

```js
<Route path="/" exact component={PageOne} />
```

is identical to

```js
<Route path="/" exact={true} component={PageOne} />
```

- Don't use anchor tags to navigate in React components. The anchor tags forces the browser to reload the whole application. Use Link component instead.

```js
<Link to="/">Navigate to PageOne</Link>
```

- with Link the React Router prevents the browser from navigating to the new page and fetching the new index.html file. The URL still changes. The History still sees the updated URL. It takes the URL and sends it to BrowserRouter which communicates the URL tou Route components. Route components rerender to show the new set of components.

- This is the nature of a Single Page Application (SPA)

### R2D40 - August 30th, 2019

#### Different React Router types

- Browser Router
  - uses everything after the top level domain or port as the `path`
- Hash Router
  - uses everything after the # as the `path
- Memory Router
  - does not use the URL to track the navigation

#### Practice project, wiring up routes

- StreamList `path: /`
- StreamCreate `path: /streams/new`
- StreamEdit `path: /streams/edit`
- StreamDelete `path: /streams/delete`
- StreamShow `path: /streams/show`

### R2D41 - August 31st, 2019

#### Practice project

- Added Header component to App component because Link component shall be a child of a Router.
  - the header component is still shown on every page because it's not wired up to a path
- The App shall have an authentication. A login button `Login with Google` shall appear on the top right in the header

#### Email/ Password Authentication

- store a record in a database with the user's email and password
- when the user tries to login we compare the email and password with what is stored in the database
- the user is logged in when a valid email-password combination is entered

#### OAuth Authentication

- user authenticates with an outside provider like GitHub, LinkedIn, Google or Facebook
- user authorizes the app to access their informaiton at that provider
- the outstide provider provides different information about the user
- we are trusting the outside provider to correctly handle the identification of a user
- OAuth can be used for
  - user identification in our application
  - making actions on behalf of the user through our application

Infos about Google OAuth can be found here https://developers.google.com/identity/protocols/googlescopes and here https://developers.google.com/identity/protocols/OAuth2

#### OAuth for Servers

- results in a `token` that a server can use to make requests on behalf of the user (same as for browser)
- used when we have an application that needs to access user data when they are **not** logged in (e.g. application that checks emails also if user is not logged in)
- difficult to setup because we need to store a lot of info about the user

#### OAuth for JavaScript browser application

- results in a `token` that a browser app can use to make requests on behalf of the user
- usually used when we have an app that only needs to access user data while they **are** logged in
- very easy to set up with Google's JavaScript library to automate flow
- my application shall have the following authentication flow

  - user clicks `Login with Google` button in browser (click event handler)
  - code calls google JS library to start the authentication via OAuth
  - the Google JS lib make an authentication request to Google platform
  - Google then shows a popup confirmation screen which the user shall accept. The popup screen then closes.
  - Google JS library invokes a callback function in our ReactJS/ Redux application. It is provided with an authorization token ans profile information for the given user. This is identifying the user and prove that the user is sucessfully logged in.
  - Logout is handled in a similar way via callback.

#### How to setup the project for OAuth with Google?

- Open console.developers.google.com and create a new project
  - wait for the project to be created and then select the project
  - create new credentials for the project
  - create OAuth client ID
  - set authorized JS origin to http://localhost:3000 for practice project
- set up an OAuth confirmation screen and generate an OAuth client ID
- install Google's API library, initialize it with the OAuth client ID
- make sure the lib gets called any time the user clicks on the `Login with Google` button
- install the google api via index.htmlheader and script tag

```html
<script src="https://apis.google.com/js/api.js"></script>
```

- open the browser console of the web application and check if google api is sucessfully loaded via `gapi`. It should return an object.
  - gapi only has one method `load`. This is so that the api can be kept very small for distribution. To receive further functionalities one must use load to retrieve them.

```js
class GoogleAuth extends React.Component {
  state = { isSignedIn: null };

  componentDidMount() {
    // wire Google API to our project
    // Loaded additional code `client:auth2
    window.gapi.load('client:auth2', () => {
        // initialize the client
      window.gapi.client
        .init({
          clientId:
            '293501909631-886gvf9254f4ltm8idakop16ntstvpae.apps.googleusercontent.com',
          scope: 'email'
        })
        .then(() => {
          this.auth = window.gapi.auth2.getAuthInstance();
          // update component level state shall rerender the component
          this.setState({ isSignedIn: this.auth.isSignedIn.get() });
        });
    });
  }
...
```

- googled for `gapi documentation` and checked out __Authentication__ 
- tried the API via browser console and already initialized client (see above).

```js
const auth = gapi.auth2.getAuthInstance();
auth.signIn(); // Google auth Popup opens
auth.isSignedIn.get(); // Is the user signed in?
```

### R2D42 - September 1st, 2019

#### Google auth

Digging a bit into the Object one receives after `gapi.auth2.getAuthInstance().isSignedIn`. The `get()` method is not shown there. This method is provided via prototype inheritence. Another interesting method in proto is `listen()`. This is a mtehod one can pass a callback function to. It will be invoked every time a authentication status is changed.

- added the listen call to my GoogleAuth component and wired it up with a callback function that updates state.

```js
...
        .then(() => {
          this.auth = window.gapi.auth2.getAuthInstance();
          // update component level state shall rerender the component
          this.setState({ isSignedIn: this.auth.isSignedIn.get() });
          this.auth.isSignedIn.listen(this.onAuthChange);
        });
    });
  }

  onAuthChange = () => {
    this.setState({ isSignedIn: this.auth.isSignedIn.get() });
  };
...
```

- tested in console manually signing in/ out to see if the status changes in the app
  - `gapi.auth2.getAuthInstance().signIn()`
  - `gapi.auth2.getAuthInstance().signOut()`

- created some helper methods to use as event handlers for onClick event in Google buttons

```js
...
onSignIn = () => {
    this.auth.signIn();
  };

  onSignOut = () => {
    this.auth.signOut();
  };
...
```
- technically it is not needed to create helper methods, bit it makes it clearer for everybody reading the code top-bottom to find out what is going on.

#### Adding the user auth status to Redux Store

- Google Auth component handles the `onSignInClick()` and `onSignOutClick()` invocations. These connect to GAPI Auth2 and trigger if the signIn status has changed via callback `onAuthChange()`
- `onAuthChange()` shall trigger Action creators `signIn()` and `signOut()`
- the Action creators shall mutate the auth state `isSignedIn: true/ false` in Redux store
- the application shall receive this information then from there

This approach is not following the Redux conventions at it's best. The Redux state shall be only updated via Action Creator and dispatches to Reducers. But this way I would have to move `changeAuth()` function to an action creator and therfor would spread the functionality of GoogleAuth outside of the component. For later GoogleAuth reference purpose I'm keeping it in the GoogleAuth component.

- added the action creators into GoogleAuth component and wired to `onAuthChange()`

- received the userId from GoogleAuth to be used in the app via `gapi.auth2.getAuthInstance().currentUser.get().getId();`

#### Redux dev tools

- installed browser extension for redux dev tools. The download and installation is described here `https://github.com/zalmoxisus/redux-devtools-extension`
  - install extension from webstore
  - go to `Advanced store setup` to wire it up in the app project root index.js file

```js
...
// applyMiddleware & compose
import { createStore, applyMiddleware, compose } from 'redux';

import App from './components/App';
import reducers from './reducers';

// compose
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const store = createStore(reducers, composeEnhancers(applyMiddleware));

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.querySelector('#root')
);
```

### R2D43 - September 2nd, 2019

#### Redux dev tools

- tried out Redux dev tools with my coding practice app
- tried out Redux dev tools with airbnb.com
- very useful to keep Redux store content over refreshes can be done with `http://localhost:3000?debug_session=<some_string>` in browser address

### R2D44 - September 3rd, 2019

#### Redux Forms

- installed redux-forms via `npm install redux-form@8.1.0` (was not recommended installing 8.2.0 at this time)

Handling inputs without Redux
- class based components with component level state
- took element content from state an put it into the input element
- when text was changed we had an onChange event which updated the state

Handling inputs with Redux
- input element has a value and an onChange handler
- handler triggers the Redux Form action creator and maintained by Redux Form Reducer
- reducer will hold the state of our input element (content of the form data)
- something like mapStateToProps to pass our content into input elements as values.
- Redux form will essentially do all of this automatically 

__How to use redux-form?__
- import into `reducer/index.js` and add it to the combineReducers object

```js
...
import { reducer as formReducer } from 'redux-form';

export default combineReducers({
  auth: authReducer,
  form: formReducer
});
```

### R2D45 - September 4th, 2019

#### Redux Forms

- added a first Field component to StreamCreate
- in `<Field component={comp} />` a component (e.g. input) has to be wired. The component receives a bunch of props including callback handlers via redux forms, this can be easily checked via `console.log(formProps)`
- whenever a property appears in Field component that is not known how to handle, Redux Form just passes it as additional property. This way it can be easily used in the render method (see label beyond) 

```js
import React from 'react';
import { Field, reduxForm } from 'redux-form';

class StreamCreate extends React.Component {
  renderInput({ input, label, meta }) {
    console.log(meta);
    return (
      <div className="field">
        <label>{label}</label>
        <input {...input} />
        <div>{meta.error}</div>
      </div>
    );
  }

  render() {
    return (
      <form className="ui form">
        <Field name="title" component={this.renderInput} label="Enter Title" />
        <Field
          name="description"
          component={this.renderInput}
          label="Enter Description"
        />
      </form>
    );
  }
}

export default reduxForm({
  form: 'streamCreate'
})(StreamCreate);
```

### R2D46 - September 5th, 2019

#### Redux Forms

- Proceeding with coding of my twitch like project. Wiring up the event handling with Redux forms.
- How to `preventDefault()` with Redux Forms? No need to call that method anymore, Redux Forms takes care about that. onSubmit() is not called with an event Object in this case, instead it has the values of the Fields inputs: 

```js
...
onSubmit(formValues) {
  console.log(formValues);
}

render() {
  return (
    <form
      onSubmit={this.props.handleSubmit(this.onSubmit)}
      className="ui form"
    >
...
```

- new method `validate(formValues)` that is used by Redux Forms to do some valdation of form Fields.

```js
const validate = formValues => {
  const errors = {};

  if (!formValues.title) {
    errors.title = 'You must enter a title';
  }
  if (!formValues.description) {
    errors.description = 'You must enter a description';
  }
  return errors;
};

export default reduxForm({
  form: 'streamCreate',
  validate
})(StreamCreate);
```

- the validate function is initially rendered or as soon the user interacts with it
- the validate function gets called with all values from the form
- if the user enters valid inputs, the validate function returns an empty object
- if the user enter invalid input, the validate function returns an object with key-name pairs (name of field as key, name has the error message to be shown) for each invalid field.
  - Redux Form then automatically rerenders the component with each Field with error showing an error message from the returned object.

### R2D47 - September 6th, 2019

#### Redux Forms

- only showing the error messages when a field is touched. This can be done with the meta property and touched

#### JSON Server package

- Streams application shall use the `json-server` package
- REST-ful conventions in the stream application and how they will be used
  - List all records: GET (route `/streams`) => Array of records
  - Get one particular record: GET (route `/streams/:id`) => Single record
  - Create record: POST (route `/streams`) => Single record
  - Update a record: PUT (route `/streams/:id`) => Single record
  - Delete a record: DELETE (route `/streams/:id`) => Nothing

#### New directory for API Server in project
The new directory has to be initialized for the use with npm. Just type `npm init` in the directory. npm creates a `package.json` that will be used to configure the new environment.
Installed the JSON Server with `npm install --save json-server`.

Created a new file in API folder called db.json. This will be used as the database for the practice project.

```json
{
  "streams": []
}
```

Created a new entry for scripts, to start the JSON server

```json
...
"scripts": {
    "start": "json-server -p 3001 -w db.json"
  },
...
```

### R2D48 - September 7th, 2019

#### Integrating JSON Server to store stream information

- installed axios and redux-thunk
- new apis folder with streams.js file. This file imports axios and stores the configuration for axios baseURL.
- new action creator for `createStream()`

```js
export const createStream = formValues => async dispatch => {
  streams.post('/streams', formValues);
};
```
- wired up Redux Thunk into root index.js

```js
...
import reduxThunk from 'redux-thunk';
...

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const store = createStore(
  reducers,
  composeEnhancers(applyMiddleware(reduxThunk))
);
...
```

#### How to wire up an action creator with Redux when it's already connected to Redux Form?

After Redux Form integration this is the status quo.

```js
export default reduxForm({
  form: 'streamCreate',
  validate
})(StreamCreate);
```

Solution 1:

```js
export default connect()(reduxForm({
  form: 'streamCreate',
  validate
})(StreamCreate));
```

Solution 2 (preferred one because easier to read/ more transparent what is happening):

```js
const formWrapped = reduxForm({
  form: 'streamCreate',
  validate
})(StreamCreate);

export default connect(
  null,
  { createStream }
)(formWrapped);
```

### R2D49 - September 8th, 2019

#### Adding reducers to consume the actions

- new type entry for `CREATE_STREAM`
- imported new type to action creator index.js
- added dispatch with action object to `createStream()` method 

#### Creating all action creators at once

- Because of RESTful conventions (see above) I was able to code all action creators at once.

```js
...
export const createStream = formValues => async dispatch => {
  const response = await streams.post('/streams', formValues);
  dispatch({ type: CREATE_STREAM, payload: response.data });
};

export const fetchStreams = () => async dispatch => {
  const response = await streams.get('/streams');
  dispatch({ type: FETCH_STREAMS, payload: response.data });
};

export const fetchStream = id => async dispatch => {
  const response = await streams.get(`/streams/${id}`);
  dispatch({ type: FETCH_STREAM, payload: response.data });
};

export const editStream = (id, formValues) => async dispatch => {
  const response = await streams.put(`/streams/${id}`, formValues);
  dispatch({ type: EDIT_STREAM, payload: response.data });
};

export const deleteStream = id => async dispatch => {
  await streams.delete(`/streams/${id}`);
  dispatch({ type: DELETE_STREAM, payload: id });
};
...
```

#### Reducer structure - Object based reducers

Instead of returning an array of streams - as practiced before - this time will return an object. Each object element will be a stream. The key for each element will be the id of the stream. With the object approach the updating process will be much more straightforward
- update => {...state, name:'Hugo'}
- adding a property => {...state, age: 30}
-- removing a property => {...state, age: undefined} or _.omit(state, 'age')

This will be used in reducer return additionally with key interpolation. Will be look like this for example:

```js
const streamReducer = (state = {}, action) => {
  switch (action.type) {
    case EDIT_STREAM:
      return {...state, [action.payload.id]: action.payload};
    default:
      return state;
  }
};
```

Important: Redux only interpretes a change if the object is really changed and not just adjusted. That's why a new object is created, the old state is spreaded, and new adjustments are included.

- Installed and used lodash to handle the DELETE_STREAM case in reducer. The omit() function creates a new state object without the deleted element.

```js
_.omit(state, action.payload);
```

- using lodash to map an Array to a new object and assing the value of a property as object key with `_.mapKeys()`

```js
_.mapKeys(action.payload, 'id');
```

### R2D50 - September 9th, 2019

#### StreamList Component

- implementing the StreamList component
- refactoring it to a class-based component so I can use the `componentDidMount()` method to trigger the action `fetchStreams()`
- created a `mapStateToProps()` method and turned the Object of streams into an array with `Object.values()`

```js
const mapStateToProps = state => {
  return { streams: Object.values(state.streams) };
};
```

- new `renderList()` method that maps the stream array and creates stream entries
- called `renderList()` then via `render()` method
- retrieving the userId from state via `getState()` in action creator

```js
...
export const createStream = formValues => async (dispatch, getState) => {
  const { userId } = getState().auth;
  const response = await streams.post('/streams', {...formValues, userId});
  dispatch({ type: CREATE_STREAM, payload: response.data });
};
...
```

- created a new helper method to find out if the mapped stream is my own stream. In such cases I want to render an edit and delete button.

```js
...
renderAdmin = stream => {
    if (stream.userId === this.props.currentUserId) {
      return <div>Edit/ Delete</div>;
    }
  };
...
```

- added a `renderCreate()` button and helper method with a link to `/streams/new`

### R2D51 - September 10th, 2019

#### Intentional vs. programmatic Navigation

*Intentional Navigation:*
User clicks on a link to move to another page.

*Programmatic Navigation:*
The user is forced to another page through code.

Create a BrowserHistory for programmatic Navigation. New file in src folder called `history.js`. This file shall have the following code:

```js
import { createBrowserHistory } from 'history';

export default createBrowserHistory();
```

This will create a history Object that can be maintained manually instead of automatically through the react-router-dom. For that it's needed to switch from `BrowserRouter` to `Router` in App.js and to use history as property fot the Router component.

### R2D52 - September 11th, 2019

#### Programmatic Navigation with history object

- imported history object in action cretor `index.js`
- used history object in `createStream()` after dispatch via `history.push('/');` which navigates to url root

#### Selection Reducer/ URL-based selection

**URL-based selection:** Put the ID of the stream being edited into the URL.
**Selection Reducer:** When a user clicks on a stream to edit it, use a `selectionReducer` to record what stream is being edited.

### R2D53 - September 13th, 2019

#### Programmatic Navigation with history object
- swapped the button element in `StreamList.js` against a tag with the `Link` component

```js
...
renderAdmin = stream => {
    if (stream.userId === this.props.currentUserId) {
      return (
        <div className="right floated content">
          <Link to={`/streams/edit/${stream.id}`} className="ui button primary">
            Edit
          </Link>
          <button className="ui button negative">Delete</button>
        </div>
      );
    }
  };
...
```

- added a small change to `App.js` and modified the path for the StreamEdit route

```js
...
<Route path="/streams/edit/:id" exact component={StreamEdit} />
...
```

- the usage of `:anything` in a route path allows to use that as variable. the colon is the magical character here
- when using react-router-dom the Route component automatically adds a bunch of props that can be used for the navigation

> With React-Router, each component needs to be designed to work in isolation. That means each component has to fetch its own data!

- one shall not assume that data might have already been loaded somehwere in the application.

### R2D54 - September 14th, 2019

#### Programmatic Navigation with history object

- making sure the `StreamEdit` component fetches the stream data beforehand
- refactored the component to a class besed component and created the `componentDidMount()` method to initially fetch the stream for the given id
- this shall be done in other components in similar war to ensure that the needed stream data is loaded initially into Redux store

```js
...
import { fetchStream } from '../../actions';

class StreamEdit extends React.Component {
  componentDidMount() {
    this.props.fetchStream(this.props.match.params.id);
  }
...
export default connect(
  mapStateToProps,
  { fetchStream }
)(StreamEdit);
```

#### Code reuse

- `StreamEdit` and `StreamCreate` components are very similiar besides 3 things
  - Title
  - input fields with or without iniial content
  - action creator that is triggered when pressing the submit button
- abstract out the form logic to a new component `StreamForm` and pass down some initial values for `StreamEdit` and a onSubmit callback function for `StreamEdit`and `StreamCreate`
- created a new component `StreamForm`
  - took everything from `StreamCreate` and created a new `StreamForm` component with different changes
- reafactored `StreamEdit` which is also wrapped withing ReduxForm
  - using sprecial props `initialValues` with keys `title` and `description` to automatically add these to `StreamEdit` properties with the same name. This a a convenient feature of ReduxForm to achieve this kind of stuff.
  - using lodash to only pick the properties needed for StreamEdit. Only updated properties shall be returned.

```js
render() {
    if (!this.props.stream) {
      return <div>Loading...</div>;
    }

    return (
      <div>
        <h3>Edit a Stream</h3>
        <StreamForm
          initialValues={_.pick(this.props.stream, 'title', 'description')}
          onSubmit={this.onSubmit}
        />
      </div>
    );
  }
```
- tested the new StreamEdit and now happens that the userId is lost after update. Debugging.
  - found that I'm using PUT request in action creator for `editStream()`. PUT always updates/ replaces all properties of a record.
  - changed to PATCH request (only updates some properties of a record) solved the issue.

```js
...
export const editStream = (id, formValues) => async dispatch => {
  const response = await streams.patch(`/streams/${id}`, formValues);
  dispatch({ type: EDIT_STREAM, payload: response.data });
  history.push('/');
};
...
```

#### Modal overlay for StreamDelete

It seems to be surprisingly difficult to create a modal overlay with React. Everything has to be nested into the div with id 'root'. A modal component would have to be nested into the page hierarchy like this example:

`body>div 'root'>Provider>App>Route>StreamDelete>Modal>Button`

A solution to get around this could be React Portals.

- created a new component file `Modal.js`

```js
import React from 'react';
import ReactDOM from 'react-dom';

const Modal = props => {
  return ReactDOM.createPortal(
    <div className="ui dimmer modals visible active">
      <div className="ui starndard modal visible active">
        Test Modal Test Modal
      </div>
    </div>,
    document.querySelector('#modal')
  );
};

export default Modal;
```

- added a div with modal id in index.html

```html
...
<body>
...
    <div id="root"></div>
    <div id="modal"></div>
...
```

- added Modal to StreamDelete component.

```js
...
import Modal from '../Modal';

const StreamDelete = () => {
  return (
    <div>
      StreamDelete
      <Modal />
...
```

- added an onClick event to outer div in Modal.js. This event shall route to `/` as soon a user clicks outside of the Modal. If the user clicks on a child element of that div, the user is also navigated back. Why?
  - this is because of the so called event propagation. As soon an event is triggered, the event is bubble up to the parents as log there is no handler found to react on it. One way to interrupt this, is to stop the propagation via `onClick={e => e.stopPropagation()` in a child element.
- using `React.Fragment` in JSX to bundle elements with a surrounding div tag. If wrapped into React.Fragment this is possible. These tags can also be shortened with `<> ... </>`

### R2D55 - September 15th, 2019

#### Working on ShowStream component

- adjusted the route in `App.js` so that the `:id` variable is available for StreamShow
- added a Link component to the StreamList entry header title. Now when clicking the link the user is navigated to the StreamShow page.
- the new route in Apps.js leads to showing an additional component when navigating to StreamCreate component. Both paths match when navigating to `localhost:3000/streams/new`

```js
...
<Route path="/streams/new" exact component={StreamCreate} />
...
<Route path="/streams/:id" exact component={StreamShow} />
...
```

- the Switch component in `react-router-dom` can help with that. Using it tells React to only render the first route that is found and matched. 

```js
...
import { Router, Route, Switch } from 'react-router-dom';
...
          <Switch>
            <Route path="/" exact component={StreamList} />
            <Route path="/streams/new" exact component={StreamCreate} />
            <Route path="/streams/edit/:id" exact component={StreamEdit} />
            <Route path="/streams/delete/:id" exact component={StreamDelete} />
            <Route path="/streams/:id" exact component={StreamShow} />
          </Switch>
...
```

### R2D56 - September 16th, 2019

#### Working on StreamShow component

- refactored initial StreamShow component to a class-based component.
- imported connect and fetchStreams action creator
- added mapStateToProps method
- exported connect

#### RMTP Server
- installed a standalone RMTP Server via `npm install --save node-media-server`
- documentation can be found on github https://github.com/illuspas/Node-Media-Server
- the following configration has to be done for singlecore mode in a index.js file

```js
const NodeMediaServer = require('node-media-server');

const config = {
  rtmp: {
    port: 1935,
    chunk_size: 60000,
    gop_cache: true,
    ping: 30,
    ping_timeout: 60
  },
  http: {
    port: 8000,
    allow_origin: '*'
  }
};

var nms = new NodeMediaServer(config)
nms.run();
```
- edit the package.json and add a start script like this

```js
...
"scripts": {
    "start": "node index.js"
  },
...
```

#### React Context System

*Props System* Gets data from a parent component to a direct child component

*Context System* Gets data from a parent component to any nested child componennt.

### R2D57 - September 17th, 2019

#### Developer Documentation @metasfresh

- creating further developer documentation in the metasfresh-webui-frontend project https://github.com/metasfresh/metasfresh-webui-frontend
- reading about Tether (react-tether) http://tether.io/ and how it is used to position elements exactly together and avoid them splitting them on a page

#### metasfresh application structure

I'm reading into metasfresh ERP frontend code to learn more about development with JavaScript, ReactJS and Redux.

- *index.jsx*
- *App.js*
- *Login.js*
- *LoginForm.js*
- *RawList.js*
- *SelectionDropdown.js*

### R2D58 - September 18th, 2019

#### Developer Documentation @metasfresh

Reading code at https://github.com/metasfresh/metasfresh-webui-frontend and learning how the frontend of metasfresh WebUI is build with ReactJS, Redux and more libraries. A lot of things i've learned in the last 8 weeks are used in this open source project. At the moment i'm using pen and paper to take notes and draw pictures. When ready I will include the notes into the developer documentation od metasfresh.

### R2D59 - September 19th, 2019

#### Debugging issue @metasfresh

Debugging an Issue in metasfresh project. Timestamps were show as number value instead of string Date/ Time format in readonly Table Cells. Found the error and replaced the formatting argument for Moment.js. Pull Request created and merged. Besides that did a code Review for another issue in the frontend repository.

### R2D60 - September 20th, 2019

#### Debugging issue @metasfresh, documenting component hierarchy

Debugged and fixed an issue needed for the Friday release of metasfresh. Replaced the hardcoded argument for a method though a constant object and used in several places.

### R2D61 - September 21st, 2019

#### Documenting component hierarchy @metasfresh

Creating the initial documetation tags in metasfresh frontend project. On the way documenting the component hierachy to have a better overview how everything works together.

Also reading about not using absolute paths in imports. Using imports like `../../../Button` can make it very error prone when restructuring a project. Since CRA 3 is is possible to use absolute import paths with a jsconfig.json adding compiler options with the baseURL. After that import statements can look like this 

```js
import Button from components/Button;
```

Will try this in the metasfresh project too.

### R2D62 - September 22nd, 2019

#### Documenting component hierarchy @metasfresh

Further going through the components structure of @metasfresh and learning more about ReactJS, Redux and how to implement such a large project. Since the beginning of the metasfresh frontend project in 2016 I've been on the concept side most of my time. It's an amaziong feeling now to learn now how the ideas and requirements I've launched in the past have been implemented in detail and how complex everything has become in such a short time.