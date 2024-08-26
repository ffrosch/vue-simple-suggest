# vue-simple-suggest

> [!CAUTION]
> This fork was done to make our own transition to Vue 3 easier by being able to fix small problems we encounter along the way. Not recommended for general use.

Forked from [@VojtechLanka/vue-simple-suggest](https://github.com/VojtechLanka/vue-simple-suggest) which was forked from [@tbl0605/vue-simple-suggest](https://github.com/tbl0605/vue-simple-suggest) which was forked from [@KazanExpress/vue-simple-suggest](https://github.com/KazanExpress/vue-simple-suggest).

## Changes compared to [@VojtechLanka/vue-simple-suggest](https://github.com/VojtechLanka/vue-simple-suggest)

```js
export default {
    ...
    compatConfig: { COMPONENT_V_MODEL: false },
    ...
    computed: {
        componentField () {
          return Object.assign({}, this.attrsWithoutListeners, {
            ...
            onInput: this.onInput,
            ...
          })
    }
}
```

## Install

```
npm i @ffrosch/vue-simple-suggest
```

## Usage

```html
<template>
  <vue-simple-suggest v-model="valueCurrent" :list="autocompleteItems" :filter-by-query="true" @update:model-select="(item) => selectedCurrent = item"/>
</template>
```

```javascript
<script>
import VueSimpleSuggest from '@ffrosch/vue-simple-suggest'

export default {
  components: { VueSimpleSuggest },
  data () {
    return {
      valueCurrent: '',
      selectedCurrent: null,
      autocompleteItems: ['Dog', 'Cat', 'Lizard']
    }
  }
}
</script>
```

All options specified by [original documentation](https://github.com/KazanExpress/vue-simple-suggest) should still work.

## Breaking changes

When the using custom input, listener bindings must be added (provided by the vue-simple-suggest component) to the input element.

For a native html input, bind the slot prop `field`:

```html
<vue-simple-suggest v-model="model" ...>
  <template #default="{ field }">
    <input v-bind="field" type="text" />
  </template>
</vue-simple-suggest>
```

For a custom input component, bind the slot prop `componentField`:

```html
<vue-simple-suggest v-model="model" ...>
  <template #default="{ componentField }">
    <my-custom-input v-bind="componentField" ... />
  </template>
</vue-simple-suggest>
```
