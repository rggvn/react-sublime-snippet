This is a fork off the original by: [jeantimex](https://github.com/jeantimex/react-sublime-snippet)


# React Development Snippets

Feeling bored with typing or even copying React codes to write React components and test cases? If you use Sublime, hope these code snippets can help you enjoy writing your React components.

The snippets follow JavaScript ES6 syntax, we don't use the old `React.createClass({...})` anymore, we write class component and functional component. Also we provide snippets to quickly write React Lifecycle functions (e.g. `componentDidMount`).

## changes:
* moved the `PropTypes` from the React import to it's own import from `prop-types`
* Added component naming based on filename
* changed tab completion from the import snippet to `im` because it's also usefull outside of react projects

## Installation ##

### Use Package Control ###

 * Make sure you have [Package Manager](https://packagecontrol.io/installation) installed
 * Launch the command palette: `⌘+shift+p` on MacOS, `ctrl+shift+p` on Windows
 * type `add repository` and add the link of this repo
 * Type `install`, select `Package Control: Install Package`
 * Type `React`, select `react-sublime-snippet`



## Snippets ##

### React ###

**ES6 Class Component** `rcc + <TAB>`<br />
![rcc](screenshots/rcc.gif)<br />
```javascript
import React, { Component } from 'react';
Import PropTypes from 'prop-types';

class ${1:Component} extends Component {
    static propTypes = {
        className: PropTypes.string,
    };

    constructor(props) {
        super(props);
    }

    render() {
        return (
            ${0}
        );
    }
}

export default ${1:Component};
```

**Functional Component** `rfc + <TAB>`<br />
![rfc](screenshots/rfc.gif)<br />
```javascript
import React from 'react';
Import PropTypes from 'prop-types';

const ${1:Component} = ({
    className = '',
}) => {
    return (
        <div>
            ${0}
        </div>
    );
};

${1:Component}.displayName = '${1:Component}';

${1:Component}.propTypes = {
    className: PropTypes.string,
};

export default ${1:Component};
```

**static propTypes** `rspt + <TAB>`
```javascript
static propTypes = {
    ${1:prop}: PropTypes.${2:string},
};
```

**static defaultProps** `rdp + <TAB>`
```javascript
static defaultProps = {
    ${1:prop}: ${2:value},
};
```

**Define Formatted Messages** `rdm + <TAB>`
```javascript
const messages = defineMessages({
    ${1:message}: {
        defaultMessage: '${2:default message}',
        description: '${3:description}',
        id: '${4:id}',
    },
});
```

**Define New Formatted Message** `rnm + <TAB>`
```javascript
${1:message}: {
    defaultMessage: '${2:default message}',
    description: '${3:description}',
    id: '${4:id}',
},
```

**componentDidMount()** `cdm + <TAB>`
```javascript
componentDidMount() {
    ${1}
}
```

**componentDidUpdate(prevProps, prevState)** `rdu + <TAB>`
```javascript
componentDidUpdate(prevProps, prevState) {
    ${1}
}
```

**componentWillMount** `rcwm + <TAB>`
```javascript
componentWillMount() {
    ${1}
}
```

**componentWillReceiveProps(nextProps)** `rcwrp + <TAB>`
```javascript
componentWillReceiveProps(nextProps) {
    ${1}
}
```

**componentWillUnmount()** `rcwum + <TAB>`
```javascript
componentWillUnmount() {
    ${1}
}
```

**componentWillUpdate(nextProps, nextState)** `rcwu + <TAB>`
```javascript
componentWillUpdate(nextProps, nextState) {
    ${1}
}
```

**shouldComponentUpdate(nextProps, nextState)** `rscu + <TAB>`
```javascript
shouldComponentUpdate(nextProps, nextState) {
    return ${1};
}
```

### Redux ###
**Redux Component** `rrc + <TAB>`<br />
![rrc](screenshots/rrc.gif)<br />
```javascript
import React, { Component, PropTypes } from 'react';
import { connect } from 'react-redux';
import {
    ${2:action} as ${2:action}Action,
} from '${3:path}';

const mapDispatchToProps = (dispatch) => {
    return {
        ${2:action}: () => {
            dispatch(${2:action}Action());
        },
    };
};

const mapStateToProps = ({ state }) => ({
    ${4:prop}: state.${4:prop}
});

export class ${1:Component} extends Component {
    render() {
        const {
            ${2:action}
        } = this.props;

        return (
            ${0}
        );
    }
}

export default connect(
    mapStateToProps,
    mapDispatchToProps
)(${1:Component});
```

**Redux Action** `rra + <TAB>`
```javascript
export const ${1:action} = (${2:payload}) => ({
    type: ${3:type},
    ${2:payload}
});
```

**Reducer** `rrr + <TAB>`
```javascript
import {
    ${2:Action}
} from '${3:path}';

const defaultState = {
    ${4:prop},
};

const ${1:Reducer} = (state = defaultState, action = {}) => {
    switch (action.type) {
        case ${5:type}:
            return {
                ...state,
            };

        default:
            return state;
    }
};

export default ${1:Reducer};
```

### Test ###
**React Test Case (chai assert and enzyme)** `rt + <TAB>`<br/>
![rt](screenshots/rt.gif)<br />
```javascript
import React from 'react';
import { assert } from 'chai';
import { shallow } from 'enzyme';
import ${1:Component} from '${2:../component}';

const sandbox = sinon.sandbox.create();

describe('${1:Component}', () => {
    afterEach(() => {
        sandbox.verifyAndRestore();
    });

    beforeEach(() => {
        ${3}
    });

    it('should render ${1:Component} correctly', () => {
        const component = shallow(
            <${1:Component} />
        );
        ${4}
    });
});
```

**React Test Describe** `rtd + <TAB>`
```javascript
describe('${1:...}', () => {
    afterEach(() => {
        ${2}
    });

    beforeEach(() => {
        ${3}
    });

    it('should ${4:...}', () => {
        ${0}
    });
});
```

**React Test it()** `rti + <TAB>`
```javascript
it('should ${1:...}', () => {
    ${0}
});
```

**import** `im + <TAB>`
```javascript
import ${1:Package} from '${2:path}';
```

## Authors

* **Yong Su** - *Box Inc.* - [jeantimex](https://github.com/jeantimex)

## License

This project is licensed under the MIT License.
