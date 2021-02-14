<template>
  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
            color="primary"
            v-bind="attrs"
            v-on="on"
        >
          добавить
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">Todo</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
              >
                <v-text-field
                  label="название задачи"
                  :rules="rules"
                  hide-details="auto"
                  v-model="title"
                />
              </v-col>
            </v-row>
            <v-row>
              <v-col
                cols="12"
              >
                <v-text-field
                  label="задача"
                  :rules="rules"
                  hide-details="auto"
                  v-model="text"
                />
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="pushMessage"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>

export default {
  name: "Creator",
  data() {
    return {
      dialog: false,
      title: "",
      text: "",
      rules: [
        value => !!value || 'Required.',
        value => (value && value.length >= 3) || 'Min 3 characters',
        value => (value && value.trim().length >= 3) || 'Min 3 characters, without space',
      ],
    };
  },
  methods: {
    pushMessage() {
      if (this.title && this.text) {
        this.$emit("add-todo", { title: this.title, text: this.text, id: Date.now(), complete: false });
        this.title = "";
        this.text = "";
        this.dialog = false;
      }
    },
  },
};
</script>
