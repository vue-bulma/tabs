# Tabs

[Tabs](http://bulma.io/documentation/components/tabs) component for Vue Bulma.


## Installation

```console
$ npm install vue-bulma-tabs --save
```


## Examples

```vue
<template>
  <tabs animation="slide" :only-fade="false">
    <tab-pane label="Pictures">Pictures Tab</tab-pane>
    <tab-pane label="Music">Music Tab</tab-pane>
    <tab-pane label="Videos" selected>Video Tab</tab-pane>
    <tab-pane label="Documents" disabled>Document Tab</tab-pane>
  </tabs>
</template>

<script>
import { Tabs, TabPane } from 'vue-bulma-tabs'

export default {
  components: {
    Tabs,
    TabPane
  }
}
</script>
```
#### Adding is-boxed or is-toggled
To add the classes `is-boxed` or `is-toggled`, add the `boxed`
or `toggled` property to the tabs element.
```vue
<template>
  <tabs animation="slide" boxed toggled>
    <tab-pane label="Pictures">Pictures Tab</tab-pane>
    <tab-pane label="Music">Music Tab</tab-pane>
    <tab-pane label="Videos" selected>Video Tab</tab-pane>
    <tab-pane label="Documents" disabled>Document Tab</tab-pane>
  </tabs>
</template>

<script>
import { Tabs, TabPane } from 'vue-bulma-tabs'

export default {
  components: {
    Tabs,
    TabPane
  }
}
</script>
```

#### Centered toggle with icons

Using the `is-center` class with `is-toggled` and `is-fullwidth`

```vue
<template>
  <tabs alignment="center" toggle size="large" isFullwidth>
    <tab-pane icon="fa fa-image" label="Pictures">
      Picture Content
    </tab-pane>
    <tab-pane icon="fa fa-music" label="Music">
      Music Content
    </tab-pane>
    <tab-pane icon="fa fa-film" label="Film">
      Film Content
    </tab-pane>
  </tabs>
</template>

<script>
import { Tabs, TabPane } from 'vue-bulma-tabs'

export default {
  components: {
    Tabs,
    TabPane
  }
}
</script>
```

## Badges

![](https://img.shields.io/badge/license-MIT-blue.svg)
![](https://img.shields.io/badge/status-stable-green.svg)

---

> [fundon.me](https://fundon.me) &nbsp;&middot;&nbsp;
> GitHub [@fundon](https://github.com/fundon) &nbsp;&middot;&nbsp;
> Twitter [@_fundon](https://twitter.com/_fundon)

