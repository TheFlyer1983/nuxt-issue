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