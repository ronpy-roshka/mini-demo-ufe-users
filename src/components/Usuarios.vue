<template >
  <div class="card">
    <div class="card-body">
      <table class="table table-hover">
        <thead>
          <tr>
            <th scope="col">
              <span
                class="btn btn-light btn-sm my-0 py-0"
                @click.prevent="loadUsers"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M13.5 2c-5.621 0-10.211 4.443-10.475 10h-3.025l5 6.625 5-6.625h-2.975c.257-3.351 3.06-6 6.475-6 3.584 0 6.5 2.916 6.5 6.5s-2.916 6.5-6.5 6.5c-1.863 0-3.542-.793-4.728-2.053l-2.427 3.216c1.877 1.754 4.389 2.837 7.155 2.837 5.79 0 10.5-4.71 10.5-10.5s-4.71-10.5-10.5-10.5z"
                  /></svg
              ></span>
            </th>
            <th scope="col">NickName</th>
            <th scope="col">Nombre</th>
            <th scope="col">Email</th>
          </tr>
        </thead>
        <tbody v-for="user in userList" :key="user.id">
          <tr>
            <td>{{ user.id }}</td>
            <td>{{ user.username }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.email }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    user: {
      type: String,
      required: false,
    },
  },
  data() {
    return {
      userList: [],
    };
  },
  created() {
    this.loadUsers();
  },
  mounted() {
    console.log(this.user);
  },
  computed: {
    sumar() {
      return this.number1 && this.number2
        ? parseInt(this.number1) + parseInt(this.number2)
        : 0;
    },
  },
  methods: {
    loadUsers() {
      fetch("https://jsonplaceholder.typicode.com/users")
        .then((response) => response.json())
        .then((json) => {
          const shuffled = json.sort(() => 0.5 - Math.random());

          this.userList = shuffled.slice(0, 4);
        });
    },
  },
  watch: {
    _ROOT_RANDOM_VALUE: function (n, o) {
      console.log(n, o);
    },
  },
};
</script>
<style lang="scss">
.seccion-uno {
  background-color: #515adb;
  padding: 0.5rem;
}
</style>