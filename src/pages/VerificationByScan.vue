<template>
  <q-page class="flex flex-center">
    <div class="row q-col-gutter-md">
      <q-card class="my-card q-mt-xs .shadow-24">
        <q-card-section>
          <q-form @submit="onSubmit" class="q-gutter-md q-pa-md">
            <div class="text-weight-bold q-mb-lg">
              To check our records and validate the legitimacy of graduate
              students, use the form below.
            </div>
            <p v-if="scannedQRCode">Scanned QR Code: {{ scannedQRCode }}</p>
            <qrcode-stream
              class="custom-qrcode-stream"
              @decode="onQRCodeScan"
            ></qrcode-stream>
            <!-- <div>
              <q-btn
                icon="verified"
                label="VERIFY"
                type="submit"
                color="primary"
                class="full-width q-mt-md"
              />
            </div> -->
          </q-form>
        </q-card-section>
        <!-- <q-card-section>
          <qrcode-stream
            class="custom-qrcode-stream"
            @decode="onDetect"
          ></qrcode-stream>
        </q-card-section> -->
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { QrcodeStream } from "vue3-qrcode-reader";
export default defineComponent({
  name: "IndexPage",
  components: {
    QrcodeStream,
  },
  data() {
    return {
      scannedQRCode: null,
    };
  }, //END OF DATA LIFE CYCLE HOOKS
  methods: {
    onSubmit() {
      console.log("HELLO");
    },
    onQRCodeScan(detectedCodes) {
      console.log("HELLO", detectedCodes);
    },
  },
});
</script>

<style scoped>
.custom-qrcode-stream {
  width: 300px; /* Set the desired width */
  height: 300px; /* Set the desired height */
}
</style>
