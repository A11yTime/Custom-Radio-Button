<template>
  <div>
    <fieldset>
      <legend>Select Finish: </legend>
      <ul role="application">
      <li v-for="item in ToDoItems" :key="item.id" class="wrapper">
        <radio-button
        :label="item.label"
        :done="item.done"
        :id="item.id"
        :name="item.name">
        </radio-button>
      </li>
    </ul>
  </fieldset>
  </div>
 

</template>

<script>
import RadioButton from './components/RadioButton.vue'
import uniqueId from "lodash.uniqueid";

export default {
  name: 'App',
  components: {
   RadioButton
  },
  data() {
    return {
      ToDoItems: [
        { id: uniqueId("todo-"), label: "Seadirt", done: false, name: "attribute_selection"},
        {
          id: uniqueId("todo-"),
          label: "Weathered White",
          done: true, name: "attribute_selection"
        },
        { id: uniqueId("todo-"), label: "White", done: false, name: "attribute_selection" },
        { id: uniqueId("todo-"), label: "Smoked charcoal", done: false, name: "attribute_selection" },
      ],
    };
  },
}
</script>


<style>
html {
  box-sizing: border-box;
  background: #f2f2f2;
  padding: 20px 50px
}

/* Inherit box-sizing to make it easier to change the property
 * for components that leverage other behavior.*/
*,
*::before,
*::after {
  box-sizing: inherit;
}

/*style form to limit width and highlight the long label*/
form {
    margin: 1rem auto;
    max-width: 750px;
}

/*style wrapper to give some space*/
.wrapper {
    position: relative;
    margin-bottom: 1rem;
    margin-top: 1rem;
}

/*style label to give some more space*/
.wrapper label {
    display: block;
    padding: 12px 0 12px 48px;
}

/*style and hide original checkbox*/
.wrapper input {
  height: 40px;
  left: 0;
  opacity: 0;
  position: absolute;
  top: 0;
  width: 40px;
}

/*position new box*/    
.wrapper input + label::before {
  border: 2px solid;
  content: "";
  height: 40px;
  left: 0;
  position: absolute;
  top: 0;
  width: 40px;
  border-radius:15px;
}

/*radio pseudo element styles*/
.wrapper input + label::after {
  content: "";
  opacity: 0;
  border: 10px solid;
  border-radius: 50%;
  position: absolute;
  left: 10px;
  top: 10px;
  transition: opacity 0.2s ease-in-out;
}

/*reveal check for 'on' state*/
.wrapper input:checked + label::after {
  opacity: 1;
}

/*focus styles*/
.wrapper input:focus + label::before {
 outline: 1px solid blue; /* For Windows high contrast mode. */
}
fieldset {
  border: none;
}
li {
    list-style: none;
}

legend {
  font-weight: bold
}
</style>
