# The Mars Gallery Page

## General idea

We'd like you to use the [NASA API](https://api.nasa.gov/) in order to display the Mars Curiosity photos. You don't necessarilly need to register for the API, as there's a free API KEY offered which you can append as a query string to all your requests. (api_key=DEMO_KEY). If you encounter any limitations with the DEMO_KEY, feel free to register, but there shouldn't be any.

## Tech/Provided code and boilerplate
This is a working APP created with vue-cli (for React devs, similar to Create React App). Just install dependencies, run `yarn serve` and start coding.

You'll find all the other available npm script commands in package.json.

We also have a (very rough) PDF mockup. (mock.pdf)

## Features
*DISCLAIMER* You don't need to complete all of the steps below. This app just serves as a basis of discussion for our technical talk in the next step. Do not spent more than 6 hours on this.

We've split our features in steps, with an increasing complexity.

### Phase 1

Use the "Mars Rover Photos" API section to load the first page of the "Curiosity" Rover photos. You can use a grid layout, similar to the mockup provided (feel free to be creative if you feel like it, but we're not after your design skills here :-) ).


### Phase 2

As there's potentially several pages of images available for some of the rovers, think of a nice UI pattern that will give the chance to the user to browse all available images. Think "Infinite". You could use a technique to 'throttle' your API requests.


### Phase 3 - nice to have

Your Product owner would like to offer some filtering to the end users. Add a sidebar/left column to your layout with a form element (please choose what you think is best: textbox, dropdown, select, radio?).  The element should give the possibility to change the Rover (Curiosity, Opportunity, Spirit)


## Things to keep mind
- use open source helper libraries at will
- you probably don't need to use a UI component library like vuetify
- find ways to minimize API requests as too many requests might result in IP blocking
- we'd like to see how you implement Data Fetching, how you structure your code, and also how your page responds to different viewports. There's definitely more than a few ways to implement most of the things so we are curious to see and discuss your decisions. Vuex is available in the project, you're free to use it, but you don't have to. (both decisions are acceptable).
- we'd like to see code like you would do for production-ready systems, so think of edge cases, UI glitches, and some basic optimizations. CSS is important: Use the latest features, we support the last two versions of popular & modern browsers.


## Deliverables

- fork the repository and/or clone it locally and work on a new private repo in your github profile. Give us permissions when you're finished. Meaningful git commits would be appreciated, so we can see your way of iterating through code.
