<template>
  <div>
    <v-row
      justify="center"
    >
      <v-btn
        color="primary"
        class="ma-2"
        icon
        @click="dialog = true"
      >
        <v-icon>mdi-pencil-plus</v-icon>
      </v-btn>

      <v-dialog
        v-model="dialog"
        max-width="500px"
      >
        <v-card>
            <v-toolbar
                color="primary"
                dark
            >
                <v-card-actions class="justify-start">
                    <v-btn
                        icon
                        text
                        @click="dialog = false"
                    >
                        <v-icon>mdi-trash-can-outline</v-icon>
                    </v-btn>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-title>
                    新しい予定
                </v-card-title>
                <v-spacer></v-spacer>
                <v-card-actions class="justify-end">
                    <v-btn
                        icon
                        text
                        @click="dialog = false, addEvent()"
                    >
                        <v-icon>mdi-calendar-edit-outline</v-icon>
                    </v-btn>
                </v-card-actions>
            </v-toolbar>

            <v-card-text>
                <div class="text-h2 pa-4">
                    <v-container fluid>
                        <v-checkbox
                          v-model="allDay"
                          label="終日の予定"
                          class="mx-auto"
                        ></v-checkbox>
                        <v-text-field
                            v-model="name"
                            counter="10"
                            hint="10文字以内"
                            label="タイトル"
                        ></v-text-field>
                        <v-row>
                          <v-col
                           cols="11"
                          >
                            <div style="pointer-events: none;">
                              <v-text-field
                                  v-model="start"
                                  label="開始"
                              ></v-text-field>
                            </div>
                          </v-col>
                          <v-col
                            cols="1"
                            class="pt-10"
                          >
                            <InputDateTime
                              :title ='startDialogTitle'
                              :allDay ='allDay'
                              @inputStart="inputStart"
                            >
                            </InputDateTime>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col
                           cols="11"
                          >
                            <div style="pointer-events: none;">
                              <v-text-field
                                  v-model="end"
                                  label="終了"
                              ></v-text-field>
                            </div>
                          </v-col>
                          <v-col
                            cols="1"
                            class="pt-10"
                          >
                            <InputDateTime
                              :title ='endDialogTitle'
                              :allDay ='allDay'
                              @inputEnd="inputEnd"
                            >
                            </InputDateTime>
                          </v-col>
                        </v-row>
                        <button style="width: 100%;" @click="colorPick = !colorPick">
                          <div style="pointer-events: none;">
                            <v-text-field
                                v-model="color"
                                label="色"
                            ></v-text-field>
                          </div>
                        </button>
                        <v-fab-transition>
                          <v-row v-show="colorPick">
                            <v-card class="px-8">
                              <v-radio-group
                                v-model="color"
                                column
                              >
                              <v-row>

                                <v-radio
                                  label="red"
                                  color="red"
                                  value="red"
                                ></v-radio>
                                <v-radio
                                  label="pink"
                                  color="pink"
                                  value="pink"
                                ></v-radio>
                                <v-radio
                                  label="purple"
                                  color="purple"
                                  value="purple"
                                ></v-radio>
                                <v-radio
                                  label="indigo"
                                  color="indigo"
                                  value="indigo"
                                ></v-radio>
                                <v-radio
                                  label="cyan"
                                  color="cyan"
                                  value="cyan"
                                ></v-radio>
                                <v-radio
                                  label="teal"
                                  color="teal"
                                  value="teal"
                                ></v-radio>
                                <v-radio
                                  label="green"
                                  color="green"
                                  value="green"
                                ></v-radio>
                                <v-radio
                                  label="lime"
                                  color="lime"
                                  value="lime"
                                ></v-radio>
                                <v-radio
                                  label="yellow"
                                  color="yellow"
                                  value="yellow"
                                ></v-radio>
                                <v-radio
                                  label="orange"
                                  color="orange"
                                  value="orange"
                                ></v-radio>
                              </v-row>
                              </v-radio-group>
                            </v-card>
                          </v-row>
                        </v-fab-transition>
                        <v-textarea
                            clearable
                            clear-icon="mdi-close-circle"
                            label="メモ"
                            counter="200"
                            hint="200文字以内"
                            v-model="memo"
                        ></v-textarea>
                    </v-container>
                </div>
            </v-card-text>
          <v-card-text>
          </v-card-text>
        </v-card>
      </v-dialog>

    </v-row>
  </div>
</template>

<script>
import InputDateTime from './InputDateTime.vue'
 export default {
  components: { InputDateTime },
    props:['formKind'],
    data () {
      return {
        dialog: false,
        startDialogTitle:'開始',
        endDialogTitle:'終了',
        colorPick: false,

        name:'',
        start:'',
        end:'',
        color:'',
        memo:'',
        allDay: false,
      }
    },
    methods:{
      inputStart(startDateTime){
        this.start = startDateTime
      },
      inputEnd(endDateTime){
        this.end = endDateTime
      },
      addEvent(){
        const newEvent = {
          name: this.name,
          start: this.start,
          end: this.end,
          color: this.color,
          memo: this.memo,
          timed: !this.allDay,
          created: new Date()
        }
        this.$emit('addEvent', newEvent)
        this.initform()
      },
      initform(){
        this.name = ''
        this.start = ''
        this.end = ''
        this.color = ''
        this.memo = ''
        this.allDay = false
      }
    }
  }
</script>

<style>
</style>