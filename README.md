# Token MultiSelect Control

> **Warning**
>
> This component is superceded by the new [MultiSelectControl](https://github.com/Code-Amp/block-components/tree/main/components/multi-select-control) in the [Block Components project](https://github.com/Code-Amp/block-components)
>
> Also [available via NPM](https://www.npmjs.com/package/@codeamp/block-components).


-------

![Demo](resources/token-multi-select-control.gif)

A multiselect control in the style of Gutenberg components - filling the gap until [G2 Components](https://github.com/ItsJonQ/g2) are ready.

This is a slightly modified version of `FormTokenField` - behaving more like a multiselect.

The main differences:
- Takes an array of value/label pairs for populating the options/suggestions
- Options are immediately shown on keyboard interaction or click event (rather than waiting for 2 characters to be entered before display)
- There is no ability to create new tokens (i.e., create a new tag from within the control itself) - you can only select from the options supplied to the control

See [Form Token Field](https://github.com/WordPress/gutenberg/tree/master/packages/components/src/form-token-field) in the Gutenberg Documentation for more information.

## Keyboard Accessibility

- `left arrow` - if input field is empty, move insertion point before previous token
- `right arrow` - if input field is empty, move insertion point after next token
- `up arrow` - select previous suggestion
- `down arrow` - open the suggestions or select next suggestion

## Properties

- `value` - An array of strings representing the options selected, as values
```javascript
[ 'post', 'page', 'product' ]
```
- `options` - An array of objects with value/label pairs
```javascript
[
	{
		value: 'post',
		label: 'Post',
	},
	{
		value: 'page',
		label: 'Page',
	},
 	{
		value: 'product',
		label: 'Product',
	},
]
```
Should support most of the properties from [Form Token Field](https://github.com/WordPress/gutenberg/tree/master/packages/components/src/form-token-field)

## Usage
First you will need to add the folder `token-multiselect-control` to your project.

You might need to install the npm package - 'dom-scroll-into-view' (depending on your version of Gutenberg), run:

```npm install 'dom-scroll-into-view'```

Then:

```jsx
import TokenMultiSelectControl from '../your/path/token-multiselect-control';
import { withState } from '@wordpress/compose';

const MyMultiSelectControl = withState( {
	value: [],
	options: [
		{
			value: 'africa',
			label: 'Africa',
		},
		{
			value: 'america',
			label: 'America',
		},
		{
			value: 'asia',
			label: 'Asia',
		},
		{
			value: 'europe',
			label: 'Europe',
		},
		{
			value: 'oceania',
			label: 'Oceania',
		},
	],
} )( ( { value, options, setState } ) => ( 
	<TokenMultiSelectControl 
		value={ value } 
		options={ options } 
		onChange={ value => setState( { value } ) }
	/>
) );
```
Then add:
```
<MyMultiSelectControl />
```
To your render method.
