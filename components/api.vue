<script>
export default {
  props: ["endpoint"],
  async created() {
    try {
      this.data = await this.$axios.$get(this.endpoint);
    } catch (error) {
      console.log(error);
    }
  },
  data() {
    return {
      data: [],
    };
  },
  methods: {
    async remove(id) {
      this.data = this.data.filter((d) => d.id !== id);
      try {
        await this.$axios.$delete(`${this.endpoint.split("?")[0]}/${id}`);
      } catch (error) {}
    },
    async create(payload) {
      this.data.unshift(payload);
      try {
        await this.$axios.$post(this.endpoint.split("?")[0], payload);
      } catch (error) {}
    },
  },
  render() {
    return this.$scopedSlots.default({
      data: this.data,
      remove: this.remove,
      create: this.create,
    });
  },
};
</script>