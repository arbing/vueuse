# useIntersectionObserver

> Detects that a target element's visibility.

## Usage

```html
<template>
  <div ref="target">
    <h1>Hello world</h1>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useIntersectionObserver } from '@vueuse/core'

export default {
  setup() {
    const target = ref(null)
    const targetIsVisible = ref(false)

    const stopObserver = useIntersectionObserver({
      target: ref,
      onIntersect: ([{ isIntersecting }], observerElement) => {
        targetIsVisible.value = isIntersecting
      },
    })

    return {
      target,
      targetIsVisible,
    }
  }
}
</script>
```

[IntersectionObserver MDN](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver/IntersectionObserver)

| State       | Type                           | Description                                                                                                 |
| ----------- | ------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| target      | `Ref<Element|null|undefined>`  | An element whose visibility within the root is to be monitored.                                             |
| onIntersect | `IntersectionObserverCallback` | A function which is called when the percentage of the target element is visible crosses a threshold.        |
| root        | `Ref<Element|null|undefined>`  | The Element or Document whose bounds are used as the bounding box when testing for intersection.            |
| rootMargin  | `string`                       | A string which specifies a set of offsets to add to the root's bounding_box when calculating intersections. |
| threshold   | `number`                       | Either a single number or an array of numbers between 0.0 and 1.0.                                          |

### Return Value

| Description | Type          | Description                      |
| ----------- | ------------- | -------------------------------- |
| stopObserve | `() => void`  | A function which stops observer. |
