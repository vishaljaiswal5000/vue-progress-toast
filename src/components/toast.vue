<template>
  <div>
    <div id="myModal" class="toast" v-if="isActive">
      <div class="modalTitle">
        <div>
          <h3>{{ title }}</h3>
        </div>
        <div>
          <span @click="dismissToast" class="close" style="cursor: pointer;"
            >&times;</span
          >
        </div>
      </div>
      <!-- <hr /> -->
      <div class="content">
        <div class="progress-bar-group">
          <progress
            class="progress"
            v-if="!isUploadCompleted"
            ref="toast-progress"
            id="toast-progress"
            :value="progress"
            max="100"
            >{{ progress }}</progress
          >
        </div>
        <div class="button-group">
          <div>
            <button v-if="!isUploadCompleted">Cancel</button>
          </div>
          <div>
            <button v-if="isUploadCompleted">View Study</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.modalTitle {
  display: flex;
  justify-content: space-between;
}
.progress {
  width: 200px;
}
.content {
  display: flex;
  justify-content: space-between;
}
.progress-bar-group {
  display: flex;
  justify-content: start;
}
.button-group {
  display: flex;
  justify-content: end;
}
.toast {
  display: block;
  position: fixed;
  padding: 20px;
  top: 10px;
  right: 10px;
  width: 350px;
  border-radius: 4px;
  background-color: white;
  box-shadow: 2px 2px silver;
  border: 1px solid silver;
  padding: 10px;
  /* color: grey; */
  opacity: 1;
  animation: toast 500ms cubic-bezier(0.23, 0.82, 0.16, 1.46);
  animation-iteration-count: 1;
}

@keyframes toast {
  0% {
    opacity: 0;
    transform: translateY(200px);
  }

  100% {
    opacity: 1;
    transform: translateY(0px);
  }
}

button {
  border: 0;
  background: none;
  box-shadow: none;
  border-radius: 0px;
  cursor: pointer;
}
</style>

<script>
export default {
  props: {
    isActive: {
      type: Boolean,
      default: false,
    },
    isUploadCompleted: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: "",
    },
    progress: {
      type: Number,
      default: 0,
    },
  },
  created() {
    console.log(this.isActive);
  },
  methods: {
    dismissToast() {
      this.$emit("setDismiss", true);
    },
  },
};
</script>
