<template>
  <q-page class="flex flex-center">
    <div class="row q-col-gutter-md">
      <q-card class="my-card q-mt-xs .shadow-24">
        <q-card-section>
          <q-form @submit="onSubmit" class="q-gutter-md q-pa-md">
            <div class="text-weight-bold">
              To check our records and validate the legitimacy of graduate
              students, use the form below.
            </div>
            <q-input
              color="teal"
              v-model="post.lastname"
              outlined
              label="LASTNAME"
              :rules="[
                (val) => (val && val.length > 0) || 'LASTNAME IS REQUIRED!',
              ]"
            >
              <template v-slot:prepend>
                <q-icon name="person" />
              </template>
            </q-input>

            <q-input
              color="teal"
              v-model="post.firstname"
              outlined
              label="FIRSTNAME"
              :rules="[
                (val) => (val && val.length > 0) || 'FIRSTNAME IS REQUIRED!',
              ]"
            >
              <template v-slot:prepend>
                <q-icon name="person" />
              </template>
            </q-input>

            <q-input
              label="BIRTHDATE"
              hint="YYYY/MM/DD"
              color="teal"
              outlined
              v-model="post.date"
              :rules="[
                (val) => (val && val.length > 0) || 'BIRTHDATE IS REQUIRED!',
              ]"
            >
              <template v-slot:append>
                <q-icon name="event" class="cursor-pointer">
                  <q-popup-proxy
                    cover
                    transition-show="scale"
                    transition-hide="scale"
                  >
                    <q-date v-model="post.date">
                      <div class="row items-center justify-end">
                        <q-btn
                          v-close-popup
                          label="Close"
                          color="primary"
                          flat
                        />
                      </div>
                    </q-date>
                  </q-popup-proxy>
                </q-icon>
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
            <!-- <qrcode-stream
              class="custom-qrcode-stream"
              @decode="onDetect"
            ></qrcode-stream> -->
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
// import { QrcodeStream } from "vue3-qrcode-reader";
export default defineComponent({
  name: "IndexPage",
  components: {
    // QrcodeStream,
  },
  data() {
    return {
      post: {
        lastname: "",
        firstname: "",
        date: "",
      },
    };
  }, //END OF DATA LIFE CYCLE HOOKS
  methods: {
    onSubmit() {
      console.log("HELLO", this.post);
    },
    // onDetect(detectedCodes) {
    //   console.log("HELLO", detectedCodes);
    // },
  }, //END OF METHODS LIFE CYCLE HOOKS
});
</script>

<style scoped>
.custom-qrcode-stream {
  width: 300px; /* Set the desired width */
  height: 300px; /* Set the desired height */
}
</style>
