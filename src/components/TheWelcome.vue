<template>
  <div>
    <div class="container">
      <div class="calculator">
        <form>
          <div class="display">
            <input type="text" v-model="display" readonly>
          </div>
          <div>
            <input type="button" value="AC" @click="clearField" class="operator">
            <input type="button" value="DE" @click="deleteCharacter" class="operator">
            <input type="button" value="." @click="appendCharacter('.') " class="operator">
            <input type="button" value="/" @click="appendCharacter('/') " class="operator">
          </div>
          <div>
            <input type="button" value="7" @click="appendCharacter('7')">
            <input type="button" value="8" @click="appendCharacter('8')">
            <input type="button" value="9" @click="appendCharacter('9')">
            <input type="button" value="*" @click="appendCharacter('*')" class="operator">
          </div>
          <div>
            <input type="button" value="4" @click="appendCharacter('4')">
            <input type="button" value="5" @click="appendCharacter('5')">
            <input type="button" value="6" @click="appendCharacter('6')">
            <input type="button" value="-" @click="appendCharacter('-')" class="operator">
          </div>
          <div>
            <input type="button" value="1" @click="appendCharacter('1')">
            <input type="button" value="2" @click="appendCharacter('2')">
            <input type="button" value="3" @click="appendCharacter('3')">
            <input type="button" value="+" @click="appendCharacter('+')" class="operator">
          </div>
          <div>
            <input type="button" value="00" @click="appendCharacter('00')">
            <input type="button" value="0" @click="appendCharacter('0')">
            <input type="button" value="=" @click="calculateResult" class="equal operator">
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: '',
    };
  },
  methods: {
    clearField() {
      this.display = '';
    },
    appendCharacter(value) {
      this.display += value;
    },
    deleteCharacter() {
      this.display = this.display.slice(0, -1);
    },
    calculateResult() {
      try {
        this.display = eval(this.display).toString();
      } catch (error) {
        this.display = 'Error';
      }
    },
  },
};
</script>

<style>
*{
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    box-sizing: border-box;
}

.container{
    width: 100%;
    height: 100vh;
    background: url('../components/1325725.png');
    display: flex;
    align-items: center;
    justify-content: center;
}

.calculator{
    background: #5F6F52;
    padding: 20px;
    border-radius: 10px;
}

.calculator form input{
    border: 0;
    outline: 0;
    width: 60px;
    height: 60px;
    border-radius: 10px;
    box-shadow: -8px -8px 15px rgba(255, 255, 255, 0.1),5px 5px 15px rgba(0, 0, 0, 0.2);
    background: transparent;
    font-size: 20px;
    color: #fff;
    cursor: pointer;
    margin: 10px;
}

form .display{
    display: flex;
    justify-content: flex-end;
    margin: 20px 0;
}


form .display input{
    text-align: right;
    flex: 1;
    font-size: 45px;
    box-shadow: none;
}
form input.equal{
    width: 145px;
}

form input.operator{
    color: #33ffd8;
}

</style>