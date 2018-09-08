<template>
    <div>
        <div class="holder">
          <form @submit.prevent="addSkill">
            <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill"/>
            <!--<input type="checkbox" id="checkbox" v-model="checked">-->
            <p class="alert" v-if="errors.has('skill')"> {{ errors.first('skill') }}</p>
          </form>
          <ul>
                <li v-for="(data, index) in skills" :key="index">{{ data.skill }}</li>
            </ul>
          <p>These are the skills that you posses</p>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Skills',
  data () {
    return {
      checked: false,
      skill: '',
      skills: [
        {'skill': 'Vue.js'},
        {'skill': 'FrontEnd developer'}]
    }
  },
  methods: {
    addSkill () {
      this.skills.push({skill: this.skill})
      this.skill = ''
      console.log('This checkbox value is: ' + this.checked)
    }
  }
}
</script>
<style scoped>
  .holder {
    background: #fff;
  }
  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3F5353;
  }
  p {
    text-align: center;
    padding: 30px 0;
    color: gray;
  }
  .container {
   box-shadow: 0px 0px 40px lightgray;}
  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: black;
    color: white
  }
  .alert {
    background-color: lightcoral;
    color: darkred;
  }
</style>
