<template>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="closeDialog">
    <template #default>
      <p>Please complete all fields.</p>
      <p>Thank you!</p>
    </template>
  </base-dialog>
  
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="enterdTitle" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          type="text"
          name="description"
          id="description"
          rows="3"
          ref="enterdDescription"
        />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="enterdLink" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResourceItem'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.enterdTitle.value;
      const enteredDescription = this.$refs.enterdDescription.value;
      const enteredLink = this.$refs.enterdLink.value;
      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }
      // instead of emitting a custom event ,we can use provide/inject
      // to call the provided function here.
      //   this.$emit(
      //     'add-resource-item',
      //     this.$refs.enterdTitle.value,
      //     this.$refs.enterdDescription.value,
      //     this.$refs.enterdLink.value
      //   );
      this.addResourceItem(enteredTitle, enteredDescription, enteredLink);
    },
    closeDialog() {
      this.inputIsInvalid = !this.inputIsInvalid;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
