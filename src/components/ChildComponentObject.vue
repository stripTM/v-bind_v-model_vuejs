<template>
  <div class="child">
    <h1>ChildComponentObject</h1>
    <h2>link (prop)</h2>
    <p>
      href: "{{ link.href }}", desc: "{{ link.desc }}", link:
      <a :href="link.href">{{ link.desc }}</a>
    </p>
    <h2>localLink (local)</h2>
    <p>
      href: "{{ localLink.href }}", desc: "{{ localLink.desc }}", link:
      <a
        :href="localLink.href"
      >{{ localLink.desc }}</a>
    </p>
    <fieldset>
      <legend>Child editor text (prop with double data binding)</legend>
      <label>
        href:
        <input type="text" ref="href" v-bind:value="value.href" v-on:input="updateLink">
      </label>
      <label>
        desc:
        <input type="text" ref="desc" v-bind:value="value.desc" v-on:input="updateLink">
      </label>
    </fieldset>
    <fieldset>
      <legend>Child editor localLink (local)</legend>
      <label>
        href:
        <input type="text" v-model="localLink.href">
      </label>
      <label>
        desc:
        <input type="text" v-model="localLink.desc">
      </label>
    </fieldset>
  </div>
</template>

<script>
export default {
  name: "ChildComponentObject",
  props: ["value", "link"],
  data() {
    return {
      localLink: { ...this.link }
    };
  },
  watch: {
    link: {
      // This will let Vue know to look inside the array
      deep: true,
      // We have to move our method to a handler field
      handler(linkUpdated){
        console.log(linkUpdated);
        this.localLink = { ...linkUpdated };
      }
    }
    
  },
  methods: {
    updateLink() {
      this.$emit('input', {
        href: this.$refs.href.value,
        desc: this.$refs.desc.value
      });
    }
  }
};
</script>