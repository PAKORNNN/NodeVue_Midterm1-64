<template>
  <div>
    <h1>Show User</h1>
    <p>id: {{ userId }}</p>
    <p>nameDog - dog breed {{ user.name }} - {{ user.lastname }}</p>
    <p>Email Dog: {{ user.email }}</p>
    <p>how to raise: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>