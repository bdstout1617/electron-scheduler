<script setup lang="ts">


</script>

<template>
  <v-card>
    <v-layout>
      <v-app-bar title="Scheduler week of 03/12/2023"></v-app-bar>

      
      <v-navigation-drawer>
        <v-list>
          <v-list-item title="Information Panel"></v-list-item>
          <v-list-item title="Hours Scheduled"></v-list-item>
          <v-list-item title="Current Week"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main>
        <v-dialog 
          v-model="dialog"
        >
          <v-card>
            <v-card-title>Login</v-card-title>
            <v-card-text>
              <v-text-field v-model="username" label="Username"></v-text-field>
              <v-text-field v-model="password" label="Password"></v-text-field>
            </v-card-text>
            <v-card-actions>
              <v-btn color="primary" block @click="checkCreds()">Login</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-container 
          v-if="connected"
          class=" justify-center align-center text-h5"
        >
          <v-table style="" density="compact">
            <thead>
              <tr>
                <th class="text-left">
                  
                </th>
                <th class="text-left">
                  Sun
                </th>
                <th class="text-left">
                  Mon
                </th>
                <th class="text-left">
                  Tue
                </th>
                <th class="text-left">
                  Wed
                </th>
                <th class="text-left">
                  Thu
                </th>
                <th class="text-left">
                  Fri
                </th>
                <th class="text-left">
                  Sat
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="tod in 24"
                :key="tod"
              >
                <td>{{ convertToTime(tod) }}</td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="sunday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="monday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="tuesday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="wednesday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="thursday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="friday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
                <td>
                  <v-checkbox
                    density="compact"
                    v-model="saturday"
                    label=""
                    :value="tod"
                  ></v-checkbox>
                </td>
              </tr>
            </tbody>
          </v-table>
          <v-divider></v-divider>
          <v-btn @click="submit">Submit</v-btn>
        </v-container>
      </v-main>
    </v-layout>
  </v-card>
</template>

<script lang="ts">
export default {
  data() {
    return {
      instructions: 'Loading',
      connected: false,
      username:'',
      password:'',
      dialog:true,
      sunday:[],
      monday:[],
      tuesday:[],
      wednesday:[],
      thursday:[],
      friday:[],
      saturday:[],
    }
  },
  methods: {
    daysOfWeek(){
      return ['sunday','monday','tuesday','wednesday','thursday','friday','saturday']
    },
    convertToTime(tod: number){
      if(tod == 12){
        return `${tod} PM`
      } else if(tod == 24){
        return `${tod-12} AM`
      }  else if(tod > 12){
        return `${tod-12} PM`
      }else {
        return `${tod} AM`
      }
    },
    checkCreds(){
      console.log('checking credentials and seeing if connected')
      this.connected = true
      this.dialog = false
    },
    updateTimes(){
      console.log('Connect to shiftboard and check each timeslot to see what is and is not available')
    },
    submit() {
      console.log('Submitting to do stuff')
      console.log(this)
    }
  }
}
</script>
<style>
</style>
