<script>
export default {
  props: {
    name: {
      type: String,
      default: "Rest Button",
    },
    link: {
      type: String,
      default: "",
    },
    data: {
      type: String,
      default: "",
    },
  },
  methods: {
    // TestURL: https://gorest.co.in//public/v2/users
    async clickevent() {
      await fetch(this.link, {
        method: "POST",
        body: JSON.stringify(this.data),
      })
        .then((response) => response.json())
        .then((data) => alert("Data: " + data));
    },
  },
};
</script>
