- [My Solution to the exercise](#my-solution-to-the-exercise)
  - [Question 1: Add logic to the “addNewItem” function that adds a new item to the shoppingList array and updates the DOM.](#question-1-add-logic-to-the-addnewitem-function-that-adds-a-new-item-to-the-shoppinglist-array-and-updates-the-dom)
    - [Thought Process](#thought-process)
  - [Question 2: Implement logic for the numberOfItems computed property to keep track of the length of the shoppingList array.](#question-2-implement-logic-for-the-numberofitems-computed-property-to-keep-track-of-the-length-of-the-shoppinglist-array)
    - [Thought Process](#thought-process-1)
  - [Question 3: Disable the "add new item button" when the list has more than 5 items by using a computed property that returns a boolean based on the length of the list. You can use the ref property to reference the list and check its length. Then, bind the disabled attribute of the button to the computed property](#question-3-disable-the-add-new-item-button-when-the-list-has-more-than-5-items-by-using-a-computed-property-that-returns-a-boolean-based-on-the-length-of-the-list-you-can-use-the-ref-property-to-reference-the-list-and-check-its-length-then-bind-the-disabled-attribute-of-the-button-to-the-computed-property)
    - [Thought Process](#thought-process-2)

# My Solution to the exercise

## Question 1: Add logic to the “addNewItem” function that adds a new item to the shoppingList array and updates the DOM.

### Thought Process
The shoppingList variable is a reactive piece of data. We can see that when the array was defined, it was wrapped with the `ref` method to make it reactive. This also means, that if we want to manipulate the data, we need to use the `value property`

```js
const addNewitem = () => {
  // Use the value property to get the array and push the new item into the array

  // We make sure that the user has actually input some text by checking whether the length of the new item is greater than 0  
  if(newItem.value.length > 0){
    shoppingList.value.push(newItem.value);
    newItem.value = "";
  }

  // Clear the input field
  newItem.value = "";
};
```

## Question 2: Implement logic for the numberOfItems computed property to keep track of the length of the shoppingList array. 

### Thought Process

We need to keep track of the `shoppingList` array as the user adds more items to it.
Then return the length of the list as the computed value for `numberOfItems`  

```js
const numberOfItems = computed(() => {
  return shoppingList.value.length
});
```

## Question 3: Disable the "add new item button" when the list has more than 5 items by using a computed property that returns a boolean based on the length of the list. You can use the ref property to reference the list and check its length. Then, bind the disabled attribute of the button to the computed property 

### Thought Process
We need to keep track of the `numberOfItems` and return either `true` or `false` based on the value.  

```js
const disable = computed(()=>{
 return numberOfItems.value >= 5 ? true : false
});
```

We then need to bind said value to our button and our form input. We can `bind` the disabled attribute using the v-bind directive.

```html
<!--Binding the disabled attribute on the button to the disable computed property-->
<button
          :class="disable?'bg-gray-500 text-gray-400':'bg-green-500 hover:bg-green-600'"
          class="text-white font-bold mt-4"
          type="submit
      "
          @click="showForm = true"
          :disabled="disable"
        >
<!--Binding the disabled propery on the input to our disable computed property-->
<input
          type="text"
          placeholder="Add a new item"
          class="px-4 py-2 text-gray-200"
          v-model="newItem"
          :disabled="disable"
        />        
```

