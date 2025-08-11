# Select Tab

Fire whenever a user selects an item out of a tabset that asynchronously updates the page. Do not use this for navigation menus as those should be covered by the [navigaion linked clicked event](../../Navigation/Navigation%20Link%20Clicked.md).

## Javascript Code

```js
// When:
// User selects an item in a tabset that asynchronously updates page. Not for navigation menu use.

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "select_tab",
  detailed_event: 'Select Tab',
  event_data: {
    identifier: "<identifier>", // REQUIRED | string | ex. 12345abcde12345
    name: "<name>", // REQUIRED | string | ex. I'm looking for a family member
    heading: "<heading>", // REQUIRED | string | ex. How can we help you today?
    index: "<index>", // REQUIRED | integer | ex 1, 5
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Maximum Length|Minimum Value|
| --- | --- | --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The computer-readable machine name of the tab. Use UUID provided by the component|`12345abcde12345`||`100`||
|**name**|`string`|recommended|The human-readable name of the tab. If user does not input one, populate with numerical index of which tab this is on the page (1-indexed). FAQs are the big one that currently need to be broken out in reporting, so getting a name for those should be the priority.|`I'm looking for a family member`||`100`||
|**heading**|`string`|required|The text heading of the tab item that was opened/closed|`How can we help you today?`||`100`||
|**index**|`integer`|recommended|The ordinal slot number of the tab item. E.g. - the top item in the tab will be slot 1. (1-indexed)|`1`, `2`, `3`, `4`, `5`|`[0-9]+`|`100`|`1`
