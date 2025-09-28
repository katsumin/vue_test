<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="10">
        <v-card>
          <v-card-title>動的パラメータ・サンプル</v-card-title>
          <v-card-text>
            <v-row>
              <v-col cols="2">
                <v-list-subheader>代表者</v-list-subheader>
              </v-col>
              <v-col cols="5">
                <v-text-field label="名前" v-model="repName"></v-text-field>
              </v-col>
              <v-col cols="3">
                <v-text-field
                  label="年齢"
                  v-model="repAge"
                  suffix="歳"
                ></v-text-field>
              </v-col>
            </v-row>

            <v-row>
              <v-col cols="2">
                <v-list-subheader>電話番号</v-list-subheader>
              </v-col>
              <v-col cols="8">
                <v-text-field label="電話番号" v-model="tel"></v-text-field>
              </v-col>
            </v-row>

            <v-row>
              <v-col cols="2">
                <v-list-subheader>メールアドレス</v-list-subheader>
              </v-col>
              <v-col cols="8">
                <v-text-field
                  label="メールアドレス"
                  v-model="mail"
                ></v-text-field>
              </v-col>
            </v-row>

            <v-row v-for="member in memberList" :key="member.id">
              <v-col cols="2">
                <v-list-subheader
                  >パラメータ {{ member.id + 1 }}件目</v-list-subheader
                >
              </v-col>
              <v-col cols="5">
                <!-- <v-text-field label="名前" v-model="member.name"></v-text-field> -->
                <v-select
                  label="キー"
                  :items="['system description', 'target', 'purl']"
                />
              </v-col>
              <v-col cols="3">
                <v-text-field
                  label="値"
                  v-model="member.age"
                  suffix="歳"
                ></v-text-field>
              </v-col>
              <v-col cols="2">
                <v-btn
                  dark
                  small
                  color="grey"
                  class="ma-2"
                  @click="removeInput(member.id)"
                >
                  <v-icon dark>mdi-minus</v-icon>
                </v-btn>
              </v-col>
            </v-row>
            <v-row justify="center">
              <v-btn dark small color="grey" class="ma-2" @click="addInput()">
                <v-icon dark>mdi-plus</v-icon>
              </v-btn>
            </v-row>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue" dark> 登録 </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from "vue";

const memberList = ref([]);
const repName = ref("");
const repAge = ref("");
const tel = ref("");
const mail = ref("");

function addInput() {
  this.memberList.push({ id: this.memberList.length, name: "", age: null });
}

function removeInput(id) {
  let inputList = this.memberList;
  inputList = inputList.filter((input) => {
    return input.id !== id;
  });
  this.memberList = this.makeNewInput(inputList);
}

function makeNewInput(inputList) {
  let newInputList = [];
  for (let i = 0; i < inputList.length; i++) {
    newInputList.push({
      id: i,
      name: inputList[i].name,
      age: inputList[i].age,
    });
  }
  return newInputList;
}
</script>
