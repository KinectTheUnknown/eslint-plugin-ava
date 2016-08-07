# Prefer using async/await instead of returning a Promise

Translations: [Français](https://github.com/avajs/ava-docs/blob/master/fr_FR/related/eslint-plugin-ava/docs/rules/prefer-async-await.md)

AVA comes with built-in support for [async functions](http://www.2ality.com/2016/02/async-functions.html) (async/await). This allows you to write shorter and clearer tests.

This rule will report an error when it finds a test that returns an expression that looks like a Promise (containing a `.then()` call), which could be simplified by using the async/await syntax.


## Fail

```js
import test from 'ava';

test(t => {
	return foo().then(res => {
		t.is(res, 1);
	});
});
```


## Pass

```js
import test from 'ava';

test(async t => {
	t.is(await foo(), 1);
});
```