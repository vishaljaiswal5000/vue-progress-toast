<template>
  <div>
    <button @click="modalAlert" id="myBtn">Open Modal</button>

    <div id="myModal" class="toast">              
        <h2>Some text in the Modal..</h2>
        <div id="button-group">
          <button>Cancel</button>
          <button>View Study</button>
        </div>
      </div>
  </div>
</template>

<style scoped>
.toast{
  display:none;
  position:fixed;
  top:10px;
  right: 10px;
  width:350px;
  border-radius: 4px;  
  background-color:#4bb543;
  padding:10px;
  color: white;  
  opacity:1;
  animation: toast 500ms cubic-bezier(.23,.82,.16,1.46);
  animation-iteration-count: 1;
}


@keyframes toast{
  0%{
    opacity:0;
    transform: translateY(200px);
  }

  100%{
    opacity:1;
    transform: translateY(0px);
  }
}
</style>

<script>
export default {
  data() {
    return {
      isUploadCompleted: false,
    };
  },
  methods: {
    modalAlert() {
      // Get the modal
      var modal = document.getElementById("myModal");

      // Get the button that opens the modal
      var btn = document.getElementById("myBtn");

      // When the user clicks on the button, open the modal
      btn.onclick = function() {
        modal.style.display = "block";
      };

      setTimeout(() => {
        modal.style.display="none";
      }, 5000);

    },
  },
  mounted: {},
};
</script>
