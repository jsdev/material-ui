---
title: Autocomplete React component
components: TextField, Popper, Autocomplete
---

# Autocomplete

<p class="description">The autocomplete is a normal text input enhanced by a panel of suggested options.</p>

The widget is useful for setting the value of a single-line textbox in one of two types of scenarios:

1. The value for the textbox must be chosen from a predefined set of allowed values, e.g., a location field must contain a valid location name: [combo box](#combobox).
2. The textbox may contain any arbitrary value, but it is advantageous to suggest possible values to the user, e.g., a search field may suggest similar or previous searches to save the user time: [free solo](#free-solo).

## Combo box

The value must be chosen from a predefined set of allowed values.

{{"demo": "pages/components/autocomplete/ComboBox.js"}}

### Playground

Each of the following examples demonstrate one feature of the Autocomplete component.

{{"demo": "pages/components/autocomplete/Playground.js"}}

### Country select

Choose one country between 248.

{{"demo": "pages/components/autocomplete/CountrySelect.js"}}

## Free solo

Set `freeSolo` to true so the textbox can contain any arbitrary value.

{{"demo": "pages/components/autocomplete/FreeSolo.js"}}

## Grouped

{{"demo": "pages/components/autocomplete/Grouped.js"}}

## Disabled options

{{"demo": "pages/components/autocomplete/DisabledOptions.js"}}

## `useAutocomplete`

For advanced customization use cases, we expose a `useAutocomplete()` hook.
It accepts almost the same options as the Autocomplete component minor all the props
related to the rendering of JSX.
The Autocomplete component uses this hook internally.

```jsx
import useAutocomplete from '@material-ui/lab/useAutocomplete';
```

- 📦 [4 kB gzipped](/size-snapshot).

{{"demo": "pages/components/autocomplete/UseAutocomplete.js", "defaultCodeOpen": false}}

### Customized useAutocomplete

WIP: to implement [this design](https://www.behance.net/gallery/27997595/Multi-select-dropdown-tags-field-with-search).

Head to [Customized Autocomplete](#customized-autocomplete) for a customization example with the Autocomplete component instead of the hook.

## Asynchronous requests

{{"demo": "pages/components/autocomplete/Asynchronous.js"}}

### Google Maps place

A customized UI for Google Maps Places Autocomplete.
For this demo, we need to load the [Google Maps JavaScript](https://developers.google.com/maps/documentation/javascript/tutorial) API.

{{"demo": "pages/components/autocomplete/GoogleMaps.js"}}

## Multiple values

Also knowned as tags, the user is allowed to enter more than 1 value.

{{"demo": "pages/components/autocomplete/Tags.js"}}

### Fixed options

In the event that you need to lock certain tag so that they can't be removed in the interface, you can set the chips disabled.

{{"demo": "pages/components/autocomplete/FixedTags.js"}}

### Checkboxes

{{"demo": "pages/components/autocomplete/CheckboxesTags.js"}}

## Customized Autocomplete

This demo reproduces the GitHub's label picker:

{{"demo": "pages/components/autocomplete/GitHubLabel.js"}}

## Highlights

The following demo relies on [autosuggest-highlight](https://github.com/moroshko/autosuggest-highlight), a small (1 kB) utility for highlighting text in autosuggest and autocomplete components.

{{"demo": "pages/components/autocomplete/Highlights.js"}}

## Customer filter

The component exposes a factory to create a filter method that can provided to the `filerOption` prop.
You can use it to change the default option filter behavior.

```js
import { createFilterOptions } from '@material-ui/lab/Autocomplete';
```

It supports the following options:

1. `config` (*Object* [optional]):
  - `config.ignoreAccents` (*Boolean* [optional]): Defaults to `true`. Remove diacritics.
  - `config.ignoreCase` (*Boolean* [optional]): Defaults to `true`. Lowercase everything.
  - `config.matchFrom` (*'any' | 'start'* [optional]): Defaults to `'any'`.
  - `config.stringify` (*Func* [optional]): Defaults to `JSON.stringify`.
  - `config.trim` (*Boolean* [optional]): Defaults to `false`. Remove trailing spaces.

In the following demo, the options need to start with the query prefix:

```js
const filterOptions = createFilterOptions({
  matchFrom: 'start',
  stringify: option => option.title,
});

<Autocomplete filterOptions={filterOptions} />
```

{{"demo": "pages/components/autocomplete/Filter.js", "defaultCodeOpen": false}}

For richer filtering mechanisms, it's recommended to look at [match-sorter](https://github.com/kentcdodds/match-sorter). For instance:

```jsx
import matchSorter from 'match-sorter';

const filterOptions = (options, { inputValue }) =>
  matchSorter(options, inputValue);

<Autocomplete filterOptions={filterOptions} />
```

## Virtualization

Search within 10,000 randomly generated options. The list is virtualized thanks to [react-window](https://github.com/bvaughn/react-window).

{{"demo": "pages/components/autocomplete/Virtualize.js"}}

## Limitations

### iOS VoiceOver

VoiceOver on iOS Safari doesn't support the `aria-owns` attribute very well.
You can work around the issue with the `disablePortal` prop.

## Accessibility

(WAI-ARIA: https://www.w3.org/TR/wai-aria-practices/#combobox)

We encourage the usage of a label for the textbox.
The component implements the WAI-ARIA authoring practices.