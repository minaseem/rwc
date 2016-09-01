# rwc
[![Build Status](https://travis-ci.org/tusharmath/rwc.svg?branch=master)](https://travis-ci.org/tusharmath/rwc)
[![npm](https://img.shields.io/npm/v/rwc.svg)](https://www.npmjs.com/package/rwc)
[![Coverage Status](https://coveralls.io/repos/github/tusharmath/rwc/badge.svg)](https://coveralls.io/github/tusharmath/rwc)

RWC is a unique mix of [Shadow DOM] + [Virtual DOM] + [Redux] to create highly performant [web-components].

[Shadow DOM]:     http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/
[Virtual DOM]:    https://github.com/paldepind/snabbdom
[Redux]:          redux.js.org
[web-components]: http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/

## Features
 - **Pure API:** A component is created using `init`, `update` & `view` which a pure functions, having no side-effects just like [ELM].
 - **Custom Events:** Supports dispatching of [CustomEvent] to communicate with the outside world.
 - **Virtual DOM:** Integrates with any virtual DOM implementation.
   
[ELM]:         elm-lang.org
[CustomEvent]: https://developer.mozilla.org/en/docs/Web/API/CustomEvent


## Installation

```bash
npm install rwc --save
```

## Usage

```js
import rwc from 'rwc'
import snabbdom from 'snabbdom'
import h from 'snabbdom/h'

// check examples to see what a patcher is
import snabbdomPatcher from './snabbdom-patcher'


const component = {
                    
  init () { /* return an intial state */},
  
  update (state, action) { /* return a new state */ },
  
  view (state, dispatchAction) { /* return the virtual dom tree */ }
                  
}

const proto = rwc.createWCProto(snabbdomPatcher, component)

// create an HTML element
const html = Object.create(HTMLElement.prototype)

// extend the HTML element and register as usual
document.registerElement('x-counter', Object.assign(html, proto))
```

{{>main}}