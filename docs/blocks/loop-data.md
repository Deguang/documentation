---
title: Loop Data Block
---

# Loop Data Block

![Loop example](https://res.cloudinary.com/chat-story/image/upload/v1642310619/automa/loop_bd2por.gif)

You can use this block when you want to do looping through data.

## Loop Through
Select which data that you want to loop, you can select between the [table](/api-reference/table.md), numbers, [google sheets](/blocks/google-sheets.md), elements, [variable](/api-reference/variables.md), or custom.

When using the custom data option, make sure you write [array](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Arrays) data type with [JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON) syntax.

**Example**
```json
["one", "two", 3, 4, { "key": "value" }]
```

And when you select the `elements` options, Automa will return an array of selectors of the elements that match the `selector` you inputted. And you can use the loop data block like below.

![Loop elements](https://res.cloudinary.com/chat-story/image/upload/v1645503764/automa/Loop_elements_1_cn74zc.png)

## Loop ID
ID to identify the loop. Use this ID when [referencing data](#accessing-data) of the loop or when using the [loop breakpoint](/blocks/loop-breakpoint) block.

## Max data
Set the limit of data to loop.

## Accessing data
After you input the data that you want to loop, data of the current iteration of the loop will be available to the blocks after it. 

And you can access this data by using the mustache tag inside an input of a block, e.g. <code v-pre>{{ loopData@loopId }}</code>. Replace the `loopId` with the id of the loop. If the data is an [object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects),
```js
{
  name: 'Foo',
  nested: {
    name: 'Bar'
  }
}
```
to access the value of it you can use <code v-pre>{{ loopData@loopId.path }}</code> syntax where the `path` is the dot notation of the object. For example:

- <code v-pre>{{ loopData@loopId.name }}</code> => `Foo`
- <code v-pre>{{ loopData@loopId.nested.name }}</code> => `Bar`

Read more: [reference data](/api-reference/reference-data.md)

### Loop Index
To access the index of the loop, use the <code v-pre>{{ loopData@loopId.$index }}</code> syntax.

## Breakpoint
To make the loop data block work as intended, you need to add a breakpoint for the loop using the [loop breakpoint block](/blocks/loop-breakpoint.md). With this breakpoint, the workflow can know where to start over the loop.
