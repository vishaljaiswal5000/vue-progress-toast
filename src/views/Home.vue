<template>
  <div>
    <button @click="modalAlert" id="myBtn">Open Modal</button>
    <toast
      :isUploadCompleted="vueToast.isUploadCompleted"
      :isActive="vueToast.isActive"
      :title="vueToast.title"
      :progress="vueToast.progress"
    ></toast>
  </div>
</template>

<script>
import toast from "../components/toast.vue";

export default {
  components: {
    toast,
  },
  data() {
    return {
      vueToast: {
        isActive: false,
        isUploadCompleted: false,
        title: "Note",
        progress: 0,
      },
    };
  },
  methods: {
    modalAlert() {
      this.vueToast.isActive = true;
      this.vueToast.title = "File is Uploading";
      this.vueToast.isUploadCompleted = false;
      this.vueToast.progress = 0;
      setTimeout(() => {
        this.vueToast.progress = 30;
        setTimeout(() => {
          this.vueToast.progress = 70;
          setTimeout(() => {
            this.vueToast.progress = 100;
            this.vueToast.isActive = true;
            this.vueToast.isUploadCompleted = true;
            this.vueToast.title = "File is Uploaded";
          }, 3000);
        }, 2000);
        // this.vueToast.isActive = true;
        // this.vueToast.isUploadCompleted = true;
        // this.vueToast.title = "File is Uploaded";
      }, 5000);
    },
  },
};
</script>
