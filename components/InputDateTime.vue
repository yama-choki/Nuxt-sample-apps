<template>
  <v-row>
    <v-dialog
      v-model="dialog"
      scrollable
      max-width="400px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          icon
          v-bind="attrs"
          v-on="on"
        >
          <v-icon>mdi-calendar-clock-outline</v-icon>
        </v-btn>
      </template>
      <v-card>
        <v-toolbar
          color="primary"
          dark
        >
          <v-card-actions class="justify-start">
            <v-btn
                icon
                text
                @click="dialog = false, deleteDateTime()"
            >
              <v-icon>mdi-trash-can-outline</v-icon>
            </v-btn>
          </v-card-actions>
          <v-spacer></v-spacer>
          <v-card-title>
              {{title}}
          </v-card-title>
          <v-spacer></v-spacer>
          <v-card-actions class="justify-end">
            <v-btn
                icon
                text
                @click="dialog = false, emitDateTime()"
            >
              <v-icon>mdi-check</v-icon>
            </v-btn>
          </v-card-actions>
        </v-toolbar>
        <v-divider></v-divider>
        <v-card-text style="height: 430px;">

            <v-row justify="center" class="mt-5" >
                <v-spacer></v-spacer>
                <v-date-picker elevation="15" v-model="picker" ></v-date-picker>
                <v-spacer></v-spacer>
            </v-row>
            <v-row justify="center" v-show="!allDay">
                <v-spacer></v-spacer>
                <v-time-picker format="24hr" elevation="15" scrollable class="mt-3" v-model="timePicker" ></v-time-picker>
                <v-spacer></v-spacer>
            </v-row>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
    props:['title', 'allDay'],
    data () {
      return {
        dialog: false,
        picker:(new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        timePicker:'00:00',
      }
    },
    computed :{
        formatDateTime(){
            const dateTime = `${this.picker} ${this.timePicker}`
            return new Date(dateTime)
        }
    },
    methods:{
        emitDateTime(){
          this.title === '開始' ? this.$emit('inputStart', this.formatDateTime) :this.$emit('inputEnd', this.formatDateTime)
          this.initDateTime()
        },
        initDateTime(){
          this.picker = (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)
          this.timePicker = '00:00'
        }
    }
  }
</script>

<style>

</style>