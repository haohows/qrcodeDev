<template>
  <div class="container">
    <div class="wrap">
      <div class="qecode border mb-4">
        <div id="qrcode"></div>
      </div>

      <div class="input-group mb-3">
        <input type="text" class="form-control" placeholder="輸入內容" v-model="url" />
        <div class="input-group-append">
          <button class="btn btn-outline-secondary" type="button" @click="createNewQR">Create</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrcodeObj: {}, 
      url: "",
    };
  },
  methods: {
    createNewQR() {
      if (this.url == "") {
        return;
      }
      this.qrcodeObj.makeCode(this.url);
      this.url = "";
    },
  },
  mounted() {
    this.qrcodeObj = new QRCode("qrcode", {
      width: 260,
      height: 260,
      colorDark: "#000000", 
      colorLight: "#fff",
      correctLevel: QRCode.CorrectLevel.H,
    });
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.qecode {
  width: 260px;
  height: 260px;
}
</style>
