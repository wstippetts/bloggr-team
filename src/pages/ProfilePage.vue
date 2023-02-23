<template>
  <div v-if="account" class="component">
    <div class="container-fluid">
      <div class="row">
        <div class="col-10">
          <p>{{ account.id }}</p>
        </div>
      </div>
    </div>

  </div>
</template>


<script>
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { AppState } from "../AppState.js";

export default {



  setup() {
    const router = useRoute();

    async function findProfileById() {
      const profileId = route.params.profileId

    }

    return {
      account: computed(() => AppState.account)
    }
  }
}
</script>


<style lang="scss" scoped></style>