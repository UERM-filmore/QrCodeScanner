<template>
  <q-page class="flex flex-center">
    <div class="row q-col-gutter-md">
      <q-card class="my-card q-mt-xl .shadow-24">
        <q-card-section>
          <q-form @submit="onSubmit" class="q-gutter-md q-pa-md">
            <q-input color="teal" outlined label="Last Name">
              <template v-slot:prepend>
                <q-icon name="person" />
              </template>
            </q-input>

            <q-input color="teal" outlined label="First Name">
              <template v-slot:prepend>
                <q-icon name="person" />
              </template>
            </q-input>

            <q-input color="teal" outlined label="Birthdate">
              <template v-slot:prepend>
                <q-icon name="event" />
              </template>
            </q-input>

            <div>
              <q-btn
                icon="verified"
                label="VERIFY"
                type="submit"
                color="primary"
                class="full-width q-mt-md"
              />
            </div>
          </q-form>
        </q-card-section>
        <q-card-section>
          <qrcode-stream
            class="custom-qrcode-stream"
            @decode="onDetect"
          ></qrcode-stream>
        </q-card-section>
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
    return {};
  }, //END OF DATA LIFE CYCLE HOOKS
  methods: {
    onSubmit() {
      console.log("HELLO");
    },
    onDetect(detectedCodes) {
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
