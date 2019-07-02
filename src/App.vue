<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>File a Complaint</h1>
          <hr />
          <div class="form-group">
            <label for="email">Mail</label>
            <input type="text" id="email" class="form-control" v-model="userData.email" />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input type="password" id="password" class="form-control" v-model="userData.password" />
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input type="number" id="age" class="form-control" v-model="userData.age" />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="message">Message</label>
          <br />
          <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
          <textarea id="message" rows="5" class="form-control" v-model="message"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="form-group">
            <label for="sendmail">
              <input type="checkbox" id="sendmail" value="SendMail" v-model="sendMail" /> Send Mail
            </label>
            <label for="sendInfomail">
              <input type="checkbox" id="sendInfomail" value="SendInfoMail" v-model="sendMail" /> Send Infomail
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="male">
            <input type="radio" id="male" value="Male" v-model="gender" /> Male
          </label>
          <label for="female">
            <input type="radio" id="female" value="Female" v-model="gender" /> Female
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
          <label for="priority">Priority</label>
          <select id="priority" class="form-control" v-model="selectedPriority">
            <option v-for="priority in priorities" v-bind:key="priority">{{ priority }}</option>
          </select>
        </div>
      </div>
      <hr />
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <app-status v-model="dataSwitch"></app-status>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <button class="btn btn-primary">Submit!</button>
        </div>
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <change-status v-model="changeStatus"></change-status>
        </div>
      </div>
    </form>
    <hr />
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Data</h4>
          </div>
          <div class="panel-body">
            <p>Mail: {{ userData.email }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre">Message: {{ message }}</p>
            <!-- style="white-space: pre makes it so line breaks save in a text area-->
            <p>
              <strong>Send Mail?</strong>
            </p>
            <ul>
              <li v-for="items in sendMail" v-bind:key="items">{{ items }}</li>
              <!-- by binding v-model="sendMail" in two inputs boxes sendMail and sendInfo as an empty array,
              we are able to add to the array by click on the inputs. example:
              say we're building a form asking for features in a house:
               -chandlier
               -fireplace
               -pool
               -sauna
               -spa
             by check eaching box, we've added them to the sendMail array. we use for loop to output all items in array.
              -->
            </ul>
            <p>Gender: {{gender}}</p>
            <p>Priority: {{ selectedPriority }}</p>
            <p>Switched: {{ dataSwitch }}</p>
            <p>Status: {{ changeStatus }}</p>
            <p>Counter: {{ counter }}</p>
            <button @click="increaseCounter">+</button>
            <button @click="decreaseCounter">_</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Switch from "./Switch";
import ChangeStatus from "./ChangeStatus";

export default {
  data() {
    return {
      userData: {
        email: "",
        password: "",
        age: 27
      },
      message: "Enter some text!",
      sendMail: [],
      counter: 0,
      gender: "Male",
      changeStatus: "Criticalll",
      selectedPriority: "Medium",
      priorities: ["High", "Medium", " Low"],
      dataSwitch: true
    };
  },
  methods: {
    increaseCounter() {
      this.counter++;
    },
    decreaseCounter() {
      this.counter--;
    }
  },
  components: {
    "app-switch": Switch,
    "change-status": ChangeStatus
  }
};
</script>

<style>
</style>
