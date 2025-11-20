<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm @submit="addContact" />
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: { ContactForm },

  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data);
        alert("Thêm liên hệ thành công!");
        this.$router.push({ name: "contactbook" });
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
.page {
  margin: 0 auto;
  max-width: 750px;
}
</style>
