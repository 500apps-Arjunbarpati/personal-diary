
<template>
  <form>
    <div class="dairy">
      <h1>welcome to Personal Diary</h1>
    </div>
    <img src="../assets/diary.jpeg" class="image" />

    <h1>{{ name }}</h1>
    <br />

    <div v-on:click="sidebarFlag = true" class="button">open diary</div>

    <section
      class="sidebar-wrapper"
      v-bind:class="sidebarFlag ? 'overlay' : ''"
    >
      <div class="sidebar">
        <h1>Add to Diary</h1>
        <button @click="sidebarFlag = false" class="close">
          <span>&times;</span>
        </button>

        <div>
          <label style="border: 1px solid grey; background-color: #999"
            >select date:</label
          >
          <input
            type="date"
            class="date"
            id="date"
            v-model="date"
          /><datepicker />
          <label>Enter your special moments:</label>

          <textarea
            v-model="diary"
            id="diary"
            placeholder="Please add"
          ></textarea>
          <br />
          <label>Image:</label>
          <div><img src="../assets/playing.jpg" class="image1" /></div>
 <!-- <div> <input type="file" class="image" style="border:1px solid #999">upload</div> -->
          <button @click="save" id="save">save</button>
        </div>
       <!-- <div> <input type="image" class="image">upload</div> -->
        <button @click="submit" class="btn">information</button>

        <!-- <p>{{ information.date }}-{{ information.diary }}</p> -->
      </div>
    </section>
  </form>
  <br />
  <div>
    <button @click="showData" class="showdata" >showdata </button>
    <h2 >Diary information</h2>
    <div class="row">
      <div
        class="col-sm-1"
        style="
          background-color: #999;
          border: 2px solid black;
          text-align: center;
        "
      >
        Date
      </div>
      <br />
      <div
        class="col-sm-4"
        style="
          background-color: yellow;
          border:2px solid black;
          text-align: center;width:100px;
        "
      >
        Diary
       
      </div>
       <!-- <div
        class="col-sm-4"
        style="
          background-color: yellow;
          border:2px solid black;
          text-align: center;width:100px;
        "
      >
        image
       
      </div> -->
    </div>
    
    <div id="showUsers"></div>
  </div>

</template>
 
<script>
import datepicker from "./datepicker.vue";

export default {
  components: { datepicker },
  data() {
    return {
      name: "Arjun",
      sidebarFlag: false,
      date: [],
      diary: [],
      image: [],
      data: [],
      information: {},
      text: "",
    };
  },
  methods: {
    submit() {
      this.text = this.data;
    },
    save() {
      let date, diary;

      date = document.getElementById("date").value;
      diary = document.getElementById("diary").value;
      // image=document.getElementById("imgage").image;

      let user_records = new Array();
      user_records = JSON.parse(localStorage.getItem("users"))
        ? JSON.parse(localStorage.getItem("users"))
        : [];
      user_records.push({
        "date": date,
        "diary": diary,
        // "image":image,
      });
      localStorage.setItem("users", JSON.stringify(user_records));

      // localStorage.setItem("date",date)
      // localStorage.setItem("diary",diary)

    
    },

  showData() {
      document.getElementById("showUsers").innerHTML = "";
      let user_records = new Array();
      user_records = JSON.parse(localStorage.getItem("users"))
        ? JSON.parse(localStorage.getItem("users"))
        : [];
      if (user_records) {
        for (let i = 0; i < user_records.length; i++) {
          let addDiv = document.createElement("div");
          addDiv.className = "row";
          addDiv.innerHTML =
            '  <div class="col-sm-1" style="padding:10px; border: 1px solid black;text-align: center;">' +
            user_records[i].date +
            '</div><div class="col-sm-4" style="padding: 10px;border: 1px solid black;text-align: center;">' +
            user_records[i].diary +
            "</div>";
            //    '</div><div class="col-sm-4" style="padding: 20px;border: 1px solid black;text-align: center;">' +
            // user_records[i].image +
            // "</div>";
          document.getElementById("showUsers").appendChild(addDiv);
        }
      }
    },
  },
};
</script>


<style scoped>
form {
  text-align: center;
  background-color: lightblue;
  /* width: 500px;
margin: 0 auto;
border-inline: 20px; */
}
.button {
  text-align: center;
  border: 1px solid green;
  color: green;
  width: 150px;
  margin: 0 auto;
  padding: 10px;
  background-color: black;
  color: white;
}
.sidebar-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 0;
  background-color: orange;
  height: 100vh;
  overflow: hidden;
  transition: all 0.3s;
}
.sidebar {
  overflow: hidden;
}
.overlay {
  width: 300px;
  box-shadow: rgba(0px, green, blue, alpha);
}
.btn {
  margin: 0 auto;
  padding: 0px;
  text-align: center;

  background-color: #999;
  width: 300px;
  border-color: honeydew;
}
.text {
  width: 400px;
}
.btn1 {
  margin: 0 auto;
  padding: 0px;
  text-align: center;
  display: grid;
  background-color: #999;
  width: 50px;
  border-color: honeydew;
}
.save {
  margin: 0 auto;
  padding: 0px;
  text-align: center;
  display: grid;
  background-color: #999;
  width: 50px;
  border-color: honeydew;
}
.image1 {
  width: 200px;
}
.showdata {
  text-align: center;
  border: 1px solid green;
  color: green;
  width: 150px;
  margin: 0 auto;
  padding: 10px;
  background-color: black;
  color: white;
}

</style>
