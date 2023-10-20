<script lang="ts" setup>
const props = withDefaults(
  defineProps<{
    disabled?: boolean;
    modelValue: object | string | number | null;
    small?: boolean;
    xSmall?: boolean;
  }>(),
  {
    disabled: false,
    small: false,
    xSmall: false
  }
);

const emit = defineEmits<{
  (e: 'update:modelValue', value: object | string | number | null): void;
}>();

const v = computed({
  get: () => props.modelValue,
  set: (value) => {
    emit('update:modelValue', value);
  }
});
</script>

<template>
  <select
    v-model="v"
    :disabled="disabled"
    :class="[
      'styled-select text-p-gray-4 transition-all duration-200 ease-in-out focus:outline-none focus:ring-1 focus:ring-p-pink',
      {
        'form-select': !small,
        'form-select-small': small,
        'form-select-x-small': xSmall,
        'opacity-50': disabled
      }
    ]"
  >
    <slot />
  </select>
</template>

<style scoped>
.styled-select {
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='100' height='100' fill='%23999999'><polygon points='0,0 100,0 50,50'/></svg>")
    no-repeat;
  background-size: 10px;
  background-position: calc(100% - 10px) 65%;
  background-repeat: no-repeat;
  background-color: #efefef;
  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;
  position: relative;
}
</style>