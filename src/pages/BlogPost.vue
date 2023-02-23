<template v-if="blog">
  <BlogCard :blog="blog" />
</template>


<script>
import { onMounted, computed } from "vue";
import { useRoute } from "vue-router";
import { AppState } from "../AppState.js";
import { blogsService } from "../services/BlogsService.js";
import { logger } from "../utils/Logger.js";

export default {
  setup() {
    const route = useRoute();
    async function getPostById() {
      try {
        const blogId = route.params.blogId
        await blogsService.getPostById(blogId)
      } catch (error) {
        logger.error(error)
      }
    }

    onMounted(() => {
      getPostById()
    })

    return {
      blog: computed(() => AppState.blog)
    }
  }
}
</script>


<style lang="scss" scoped></style>