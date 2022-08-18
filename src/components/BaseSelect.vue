<template>
    <label v-if="label">{{ label }}</label>
      <select :value="modelValue" class="field" v-bind="{
        ...$attrs,
        // !! 'onChange' stands for @change, 'onInput' stands for @input etc.
        onChange: ($event) => { $emit('update:modelValue', $event.target.value) }
        }">
        <option
          v-for="option in options"
          :value="option"
          :key="option"
          :selected="option === modelValue"
        >{{ option }}</option>
      </select>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
    },
    // We make this options prop so we can receive this information from the parent.
    options: {
      type: Array,
      required: true
    }
  }
}

</script>
