<template>
  <div class="flex flex-col justify-center">
    <p class="text-2xl text-center m-2">
      {{ complaint.title }}
    </p>
    <p class="text-center">
      {{ complaint.description }}
    </p>
    <p class="text-center text-lg my-4">
      Status - <span class="bg-green-300 p-2">{{ complaint.status }}</span>
    </p>
    <p v-if="complaint.managedBy" class="text-center text-lg my-4">
      Managed By - <span class="bg-purple-300 p-2">{{ complaint.managedBy.firstName + ' ' + complaint.managedBy.lastName }}</span>
    </p>
    <div class="flex justify-center items-center my-5">
      <t-button type="button" class="mx-2" variant="error" @click="deleteComplaintUtil">
        Delete
      </t-button>
      <t-button type="button" class="mx-2" @click="updateComplaintUtil">
        Update
      </t-button>
    </div>
  </div>
</template>
<script>
export default {
  name: "ComplaintCard",
  props: {
    complaint: {
      type: Object,
      required: true,
    },
  },
  methods: {
    deleteComplaintUtil() {
      this.$emit('deleteComplaint', this.complaint._id);
    },
    updateComplaintUtil() {
      this.$emit('updateComplaint', this.complaint._id);
    }
  }
};
</script>
