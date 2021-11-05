<template>
  <h3>Vue & SignupForm </h3>

    <div>
    <form action="#">

        <label for="name">Full Name</label>
        <input type="text" id="name" name="name" placeholder="Your full name.." required v-model="name">

        <label for="email">Email</label>
        <input type="email" id="email" name="email" placeholder="Your email.." required v-model="email">      

        <label for="password">Password</label>
        <input type="password" id="password" name="password" placeholder="Your password.." required v-model="password">

        <label for="country">Country</label>
        <select id="country" name="country" required v-model="country">
          <option value="australia">Denmark</option>
          <option value="canada">Still Denmark</option>
          <option value="Denmark">No other than Denmark</option>
        </select>

        <label for="skills">Skills</label>
        <input type="text" @keyup.alt="addSkill" required v-model="tempSkill">
        
        <ul v-for="skill in skills" :key="skill" class="a">
          <li @click="deleteListItem(skill)" >{{ skill }}</li>  
        </ul>         

        <hr>

         <label class="container">accept terms and conditions
          <input type="checkbox" required v-model="terms">
          <span class="checkmark checkbox"></span>
        </label>

        <label class="container title"> favorite animals </label>
        <label class="container">Dogs
          <input type="checkbox" value="dogs" required v-model="animals">
          <span class="checkmark checkbox"></span>
        </label>
        <label class="container">Cats
          <input type="checkbox" value="cats" required v-model="animals">
          <span class="checkmark checkbox"></span>
        </label>
        <label class="container">Birds
          <input type="checkbox" value="birds" required v-model="animals">
          <span class="checkmark checkbox"></span>
        </label>

        <label class="container title"> NIGHT or DAY :</label>
        <label class="container">DAY
          <input type="radio" value="day" name="radio" required v-model="daytime">
          <span class="checkmark radio"></span>
        </label>

        <label class="container">NIGHT
          <input type="radio" value="night" name="radio" required v-model="daytime">
          <span class="checkmark radio"></span>
        </label> 
    
        <input type="submit" value="Submit">
    </form>
    <p> Email: {{ email }}</p>
    <p> Password: {{ password }}</p>
    <p> Full Name: {{ name }}</p>
    <p> Country: {{ country }}</p>
    <p> Terms: {{ terms }}</p>
    <p> Animals: {{ animals }}</p>
    <p> Day Time: {{ daytime }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            name: '',
            country: '',
            animals: [],            
            daytime: '',
            terms: '',
            skills: [],
            tempSkill: ''
        }
    },
    methods: {
      addSkill(e) {
        console.log(e)
        if(e.key === ',' && this.tempSkill){
          this.skills.push(this.tempSkill)
          this.tempSkill=''
        }

      },
      deleteListItem(item) {
        //console.log(e)
        var index = this.skills.indexOf(item);
        if (index > -1) {
          this.skills.splice(index, 1);
        }
      }
    }

}
</script>

<style>
/* Default div style*/
div {
  border-radius: 5px;
  background-color: #74d4b4;
  padding: 20px;
}

/* Input fields, Select field */
input, select{
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
/* Submit Button */
input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
input[type=submit]:hover {
  background-color: #45a049;
}

 /* Customize the label (the container) */
.container {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 16px;
  text-transform: uppercase;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.title {
  font-weight: 800;
}
/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #eee;
}

/* Create a custom radio button */
.radio {  
  border-radius: 50%;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #0a7c43;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.checkbox:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
} 

/* Style the indicator (dot/circle) */
.radio:after {
  top: 9px;
  left: 9px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: white;
}

/* List marked with bullets */
ul.a {
  list-style-type: square;
}

</style>