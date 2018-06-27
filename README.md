# Fragments and Portals

## Problem Statement


## Fragments

It is required that every React component must return a single JSX element, and
we often use the HTML-like elements such as `div`. When rendered, this creates a
DOM element for that outer `div`, which is sometimes unnecessary.

```js
class ChildComponent extends Component {
  render() {
    return (
      <div>
        <p>Hey, I am a child</p>
        <p>My name is child component</p>
      </div>
    )
  }
}

class ParentComponent extends Component {
  render() {
    return (
      <div className="parent">
        <ChildComponent />
        <ChildComponent />
      </div>
    )
  }
}
```

This set up creates a DOM structure that looks like this:

```html
<div class="parent">
  <div>
    <p>Hey, I am a child</p>
    <p>My name is child component</p>
  </div>
  <div>
    <p>Hey, I am a child</p>
    <p>My name is child component</p>
  </div>
</div>
```

Those nested `div`s don't have any purpose here and don't have any styling.
Without them though, we would have an error as there are _two_ `p` tags being
returned in the ChildComponent. Instead, we could use JSX Fragments,
preventing the extra `div`s from being added to the DOM:

```js
class ChildComponent extends Component {
  render() {
    //The wrapping 'div' here has been replaced with a React fragment
    return (
      <>
        <p>Hey, I am a child</p>
        <p>My name is child component</p>
      </>
    )
  }
}

class ParentComponent extends Component {
  render() {
    return (
      <div>
        <ChildComponent />
        <ChildComponent />
      </div>
    )
  }
}
```

With the fragment in place, the DOM will now look like this:

```html
<div>
    <p>Hey, I am a child</p>
    <p>My name is child component</p>
    <p>Hey, I am a child</p>
    <p>My name is child component</p>
</div>
```

The `<>` and `</>` are shorthand for `<React.Fragment>` and `</React.Fragment>`
and can be used interchangeably. They allow a component to return multiple
elements _without_ adding a wrapper element that adds to the DOM.


### Objective 1
Content moving student to objective 1

### Objective 2
Content moving student to objective 2

#### Key Terms (if applicable)

#### Resources (if applicable)

### Conclusion
