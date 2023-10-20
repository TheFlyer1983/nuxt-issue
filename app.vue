<script setup lang="ts">
type Data = {
  country_of_residence: string | null;
}

const countries = ['England', 'Scotland', 'Wales', 'Northern Ireland'];

const data = ref<Data>({
  country_of_residence: null
});
</script>

<template>
  <div>
    <StyledSelect v-model="data.country_of_residence">
      <option :value="null">Country of Residency</option>
      <option
        v-for="option in countries"
        :key="option"
        :value="option"
      >
        {{ option }}
      </option>
    </StyledSelect>
  </div>
</template>
