### computed property name


- case 1


```
import React, { useState } from 'react';

function SomeComponent() {
	const [state, setState] = useState({
		id: '',
		password: '',
	});

	const handleChange = (e) => {
		setState({
			[e.target.name]: e.target.value,
		});
	};

	return (
		<React.Fragment>
			<input value={state.id} onChange={handleChange} name="name" />
			<input value={state.password} onChange={handleChange} name="password" />
		</React.Fragment>
	);
}

export default SomeComponent;

```
-> [e.target.name] 이 계산된 값.의 property
-> onChange를 


- case 2

```
const noop = createAction('INCREMENT');

const reducer = handleActions(
	{
		[noop]: (state, action) => ({
			counter: state.counter + action.payload,
		}),
	},
	{ counter: 0 },
);

```

- case 3

```
import Vuex from 'vuex';
import { SOME_MUTATION } from './mutation-types';

export const SOME_MUTATION = 'SOME_MUTATION';

const store = new Vuex.Store({
	state: {
		// some code...
	},
	mutations: {
		[SOME_MUTATION](state) {},
	},
});

```

- case 4

```
const funcName0 = 'func0';
const funcName1 = 'func1';
const funcName2 = 'func2';

const obj = {
	[funcName0]() {
		return 'func0';
	},
	[funcName1]() {
		return 'func1';
	},
	[funcName2]() {
		return 'func2';
	},
};

for (let i = 0; i < 3; i++) {
	console.log(obj[`func${i}`]());
}
```


-> computed property name이라는 건 import해서 쓰는 값과 식을 넣도록 하는 것임
-> 라이브러리에서 가져다쓰는 name들을 동작 코드들이 어떻게 변경되는지(내부적으로) 알고 있으면 좋다.
