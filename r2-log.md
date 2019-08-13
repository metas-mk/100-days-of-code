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
