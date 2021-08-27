
<template>
  <form>
    <div class="dairy">
      <h1>welcome to Personal Diary</h1>
    </div>
      <img src="../assets/diary.jpeg" class="image"/>
    <h1>{{ name }}</h1>
    
    <br>
  
    <div v-on:click="sidebarFlag = true" class="button">open diary</div>

     

    <section
      class="sidebar-wrapper"
      v-bind:class="sidebarFlag ? 'overlay' : ''">
      <div class="sidebar">
       
        <h1>Add to Diary</h1>
        <button @click="sidebarFlag =false" class="close">
          <span>&times;</span>
        </button>


        <div>
          <label>select date:</label>
          <input type="date" class="date" v-model="date" /><datepicker />
          <label>Enter your special moments:</label>
         
           <textarea v-model="diary" placeholder="Please add"></textarea>
<br>
          <label>Image:</label>
          <div><img src="../assets/playing.jpg" class="image1"/></div>
          
          <button @click="save" >save</button>
         
        </div>
    <button @click="submit" class="btn" >information</button>
         <p>{{information.diary}}-{{information.date}}</p>
      
      </div>
     
    </section>
   
  </form>
 
</template>
 
<script>
import datepicker from "./datepicker.vue";


export default {
  components: { datepicker ,

  },
  data() {
    return {
      name: "Arjun",
      sidebarFlag: false,
      date: '',
      diary: '',
      image: "",
      data:[],
      information: {},
      text:''
    
    };
  },
  methods:{

 
  submit() {
   this.text=this.data;
  },
  save() {
    this.information.date = this.date;
    this.information.diary= this.diary;
    this.data.push(this.information)
   
  },
}
}
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
.image1{
  width: 200px;
}

</style>
