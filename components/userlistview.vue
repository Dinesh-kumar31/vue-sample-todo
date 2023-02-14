<template>
  <table class="table table-light">
    <tbody>
      <tr v-for="(user, index) in userList" :key="user.firstName">
        <td>{{ index + 1 }} -</td>
        <td>
          <ul class="p-0">
            <li>Full Name: {{ user.firstName }} {{ user.lastName }}</li>
            <li>Email: {{ user.email }}</li>
            <li>Age: {{ user.age }}</li>
            <li>Country: {{ user.country }}</li>
            <li>Open to remote work: {{ user.remoteWork }}</li>
            <li>Division: {{ user.division }}</li>
            <li>Profile Summary: {{ user.profileSummary }}</li>
          </ul>
        </td>
        <td>
          <button
            @click="deleteUser(user)"
            type="button"
            class="btn btn-secondary btn-sm"
          >
            Delete
          </button>
        </td>
      </tr>
      <tr v-if="!userList.length">
        <td class="text-center">No User Found</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "userlistview",
  props: ["userListData"],
  data() {
    return {
      userList: this.userListData,
    };
  },
  methods: {
    deleteUser(user) {
      this.userList = JSON.parse(JSON.stringify(this.userList)).filter(
        (e) => e.id !== JSON.parse(JSON.stringify(user)).id
      );
    },
  },
};
</script>
