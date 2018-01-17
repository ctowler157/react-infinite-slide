# React infinite slide
> if you just want infinite slider, this is is for you

[![Build Status](https://travis-ci.org/jkvim/react-infinite-slide.svg?branch=master)](https://travis-ci.org/jkvim/react-infinite-slide.js)
[![NPM version][npm-image]][npm-url]
[![Downloads][downloads-image]][npm-url]
[![Licence][licence-image]][npm-url]

[npm-url]: https://npmjs.org/package/react-infinite-slide
[downloads-image]: http://img.shields.io/npm/dm/react-infinite-slide.svg
[npm-image]: http://img.shields.io/npm/v/react-infinite-slide.svg
[licence-image]: 	https://img.shields.io/npm/l/react-infinite-slide.svg

## Feature
- swipe support
- autopaly
- allow custom arrow and dots

## Demo
[react-infinite-slide-demo](http://jkvim.github.io/react-infinite-slide)

## Install
    npm install react-infinite-slide

## Components
### `Slides`
The slides wrapper

| props      | description                                           | type            | default |
|------------|-------------------------------------------------------|-----------------|---------|
| width      | width of wrapper and slides, use "px" or "%" as unit  | String          | "500px" |
| height     | height of wrapper and slides, use "px" or "%" as unit | String          | "300px" |
| duration   | transition duration                                   | Number          | 300     |
| autoplay   | should autoplay the slides                            | Bool            | false   |
| delay      | the autoplay delay of between slides                  | Number          | 1000    |
| arrowLeft  | the left arrow component constructor                  | ReactComponent  | null    |
| arrowRight | the right arrow compnent constructor                  | ReactComponent  | null    |
| dots       | the dots component constructor                        | React Component | null    |

**Example**
```jsx
import { ArrowLeft, ArrowRight, Dots, Slides } from 'react-infinite-slide';

function App() {
  return (
    <Slides arrowLeft={<ArrowLeft />}
            arrowRight={<ArrowRight />}
            dots={<Dots />}
            duration={1000}
            height="300px"
            width="500px">
     <div className="one"></div>
     <div className="two"></div>
     <div className="three"></div>
   </Sildes>
  );
}

```

### `ArrowLeft`
This is default left arrow component, you can pass it to `Slides` as 
props of `arrowLeft`, or you can custom your `ArrowLeft` component,
`Slides` will inject `onClick` as props, and you **MUST** call it
when arrow is be clicked.

**Example**
```jsx
function ArrowLeft({ onClick }) {
  return (
    <div onClick={onClick></div>
  )
}
```

### `ArrowRight`
This is default right arrow component, you can pass it to `Slides` as 
props of `arrowRight`, or you can custom your `ArrowRight` component 
like [ArrowLeft](#arrowleft)


### `Dots`
This is default dots component, you can pass it to `Slides` as props of `dots`,
or you can custom your `Dots` component, `Slides` will inject `onClick` to
it and you **MUST** call `props.onClick(index)` when dot is be clicked. parameter
`index` is the index of the slide, *SHOULD* start from 0, like below example


**Example**
```jsx
class Dots extends React.Component {
  render() {
    return (
      <ul>
        <li key="0" onClick={() => this.props.onClick(0)}></li>
        <li key="1" onClick={() => this.props.onClick(1)}></li>
        <li key="2" onClick={() => this.props.onClick(2)}></li>
      </ul>
    );
  }
}
```