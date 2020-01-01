<template>
  <div class="child">
    <h1>ChildComponentPrimitive</h1>
    <h2>text (prop)</h2>
    <p>text: "{{ text }}"</p>
    <h2>editText (local)</h2>
    <p>text: "{{ localText }}"</p>
    <fieldset>
      <legend>Child editor text (prop with double data binding)</legend>
      <label>
        text:
        <input
          type="text"
          v-bind:value="value"
          v-on:input="$emit('input', $event.target.value)"
        >
      </label>
    </fieldset>
    <fieldset>
      <legend>Child editor localText (local)</legend>
      <label>
        text:
        <input type="text" v-model="localText">
      </label>
    </fieldset>
  </div>
</template>

<script>
export default {
  name: "ChildComponentPrimitive",
  props: ["value", "text"],
  data() {
    return {
      localText: this.text
    };
  },
  watch: {
    text(textUpdated) {
      this.localText = textUpdated
    }
  }
};
</script>