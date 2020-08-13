<template>
  <v-row align="start">
    <v-col>
      <v-data-table
        :headers="headers"
        :items="lands"
        :items-per-page="10"
        class="elevation-1"
      >
        <template v-slot:top>
          <v-toolbar flat color="white">
            <v-toolbar-title>My Lands</v-toolbar-title>
            <v-divider class="mx-4" inset vertical></v-divider>
            <v-spacer></v-spacer>
            <v-dialog v-model="dialog" max-width="500px">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  color="primary"
                  dark
                  class="mb-2"
                  v-bind="attrs"
                  v-on="on"
                  >New Land</v-btn
                >
              </template>
              <v-card>
                <v-card-title>
                  <span class="headline">{{ formTitle }}</span>
                </v-card-title>

                <v-card-text>
                  <v-container>
                    <v-row>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.landName"
                          label="Land name"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.coordination"
                          label="Coordination"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.area"
                          label="Area"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.landmark"
                          label="landmark"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6" md="4">
                        <v-text-field
                          v-model="editedItem.owner"
                          label="Owner"
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="blue darken-1" text @click="close"
                    >Cancel</v-btn
                  >
                  <v-btn color="blue darken-1" text @click="save">Save</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-toolbar>
        </template>
        <template v-slot:item.actions="{ item }">
          <v-icon small class="mr-2" @click="editItem(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="deleteItem(item)">
            mdi-delete
          </v-icon>
        </template>
        <template v-slot:no-data>
          <v-btn color="primary" @click="initialize">Reset</v-btn>
        </template>
      </v-data-table>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      dialog: false,
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'Land Name', value: 'landName' },
        { text: 'coordination', value: 'coordination' },
        { text: 'area', value: 'area' },
        { text: 'landmark', value: 'landmark' },
        { text: 'Owner Address', value: 'ownerAddress' },
        { text: 'Actions', value: 'actions', sortable: false },
      ],
      lands: [
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
        {
          id: 230,
          landName: 'KitKat',
          coordination: '30.049963, 31.262597',
          area: 65,
          landmark: 7,
          ownerAddress: 'sdko weio wwe',
        },
      ],
      editedIndex: -1,
      editedItem: {
        landName: '',
        coordination: '',
        area: 0,
        landmark: '',
        owner: '',
      },
      defaultItem: {
        landName: '',
        coordination: '',
        area: 0,
        landmark: '',
        owner: '',
      },
    }
  },
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'New Land' : 'Edit Land'
    },
  },

  watch: {
    dialog(val) {
      val || this.close()
    },
  },
  methods: {
    editItem(item) {
      this.editedIndex = this.lands.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem(item) {
      const index = this.lands.indexOf(item)
      confirm('Are you sure you want to delete this item?') &&
        this.lands.splice(index, 1)
    },

    close() {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.lands[this.editedIndex], this.editedItem)
      } else {
        this.lands.push(this.editedItem)
      }
      this.close()
    },
  },
  head: {
    title: 'Lands',
  },
}
</script>

<style type="text/scss"></style>
