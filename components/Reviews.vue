<template>
  <div>
    <h3>Customer Reviews</h3>
    <div v-if="!$fetchState.pending">
      <ReviewCard
        v-for="reviewer in reviewers.results"
        :key="reviewer.login.uuid"
        :review="reviewer"
      />
    </div>
    <div v-else>loading...</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      reviewers: [],
    };
  },
  async fetch() {
    this.reviewers = await fetch(
      "https://randomuser.me/api/?results=5"
    ).then((res) => res.json());
    console.log(this.reviewers);
  },
};
</script>

<style lang="scss" scoped></style>
