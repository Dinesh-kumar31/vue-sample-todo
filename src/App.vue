<template>
  <div class="container-fluid">
    <div class="row p-5">
      <div class="col-md-6 col-lg-6">
        <h1 class="text-center mb-3 text-primary text-decoration-underline">
          USER FORM
        </h1>
        <form @submit.prevent="addUser" class="row">
          <div class="col-md-6 col-lg-6">
            <div class="mb-3">
              <label for="first-name" class="form-label">First Name</label>
              <input
                type="text"
                class="form-control"
                id="first-name"
                placeholder="First Name"
                v-model="formValues.firstName"
              />
            </div>
          </div>
          <div class="col-md-6 col-lg-6">
            <div class="mb-3">
              <label for="last-name" class="form-label">Last Name</label>
              <input
                type="text"
                class="form-control"
                id="last-name"
                placeholder="Last Name"
                v-model="formValues.lastName"
              />
            </div>
          </div>
          <div class="col-md-6 col-lg-6">
            <div class="mb-3">
              <label for="email" class="form-label">Email</label>
              <input
                type="email"
                class="form-control"
                id="email"
                placeholder="Email"
                v-model="formValues.email"
              />
            </div>
          </div>
          <div class="col-md-6 col-lg-6">
            <div class="mb-3">
              <label for="age" class="form-label">Age</label>
              <input
                type="number"
                class="form-control"
                id="age"
                placeholder="Age"
                v-model="formValues.age"
              />
            </div>
          </div>
          <div class="col-md-6 col-lg-6">
            <div class="mb-3">
              <label for="country">Country</label>
              <select
                name="country"
                v-model="formValues.country"
                class="form-select"
                aria-label="Select Country"
              >
                <option value="" disabled selected>Select Country</option>
                <option value="India">India</option>
                <option value="USA">USA</option>
                <option value="UAE">UAE</option>
              </select>
            </div>
          </div>
          <div class="col-md-6 d-flex align-items-center col-lg-6">
            <div class="form-check">
              <input
                class="form-check-input"
                type="checkbox"
                id="remote-work"
                v-model="formValues.remoteWork"
              />
              <label class="form-check-label" for="remote-work">
                Open to work in remote
              </label>
            </div>
          </div>
          <div class="col-lg-6 col-md-6 d-flex mb-3">
            <div class="form-check">
              <input
                class="form-check-input"
                type="radio"
                name="division"
                id="software"
                value="Software"
                v-model="formValues.division"
              />
              <label class="form-check-label" for="software"> Software </label>
            </div>
            <div class="form-check ms-3">
              <input
                class="form-check-input"
                type="radio"
                name="division"
                id="hardware"
                value="Hardware"
                v-model="formValues.division"
              />
              <label class="form-check-label" for="hardware"> Hardware </label>
            </div>
          </div>
          <div class="col-12">
            <label for="profile-summary" class="form-label"
              >Profile Summary</label
            >
            <textarea
              class="form-control h-50"
              name="profilesummary"
              id="profile-summary"
              cols="30"
              rows="5"
              v-model="formValues.profileSummary"
            ></textarea>
          </div>
          <button type="submit" class="btn btn-primary">Add</button>
        </form>
      </div>
      <div class="col-md-6 col-lg-6">
        <userListView :userListData="userList"></userListView>
        <!-- <table class="table table-light">
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
        </table> -->
      </div>
    </div>
  </div>
</template>

<script>
import userListView from "../components/userlistview.vue";
export default {
  data() {
    return {
      formValues: {
        firstName: "",
        lastName: "",
        email: "",
        age: null,
        country: "",
        remoteWork: false,
        division: "",
        profileSummary: "",
        id: null,
      },
      userList: [],
    };
  },
  mounted() {
    this.formFieldsCopy = { ...this.formValues };
  },
  methods: {
    addUser() {
      this.formValues.id = Math.round(Math.random() * 10 * 12);
      this.userList.push(JSON.parse(JSON.stringify(this.formValues)));
      this.resetFormFields();
    },
    // deleteUser(user) {
    //   this.userList = JSON.parse(JSON.stringify(this.userList)).filter(
    //     (e) => e.id !== JSON.parse(JSON.stringify(user)).id
    //   );
    // },
    resetFormFields() {
      this.formValues = { ...this.formFieldsCopy };
    },
  },
  components: {
    userListView,
  },
};
</script>
