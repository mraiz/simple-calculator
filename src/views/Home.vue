<template>
  <div class="home">
    <div class="main-wrapper">
      <div class="content">
        <form>
          <div class="form-group mt-3">
            <div class="d-flex">
              <div class="wrap-input">
                <input type="number" class="form-control" v-model="valueFirst">
              </div>

              <div class="wrap-input check">
                <input type="checkbox" class="form-check-input pl-3" value="valueFirst" v-model="check_Checked" @click="resetResult">
              </div>
            </div>
          </div>

          <div class="form-group mt-3">
            <div class="d-flex">
              <div class="wrap-input">
                <input type="number" class="form-control" v-model="valueSecond">
              </div>

              <div class="wrap-input check">
                <input type="checkbox" class="form-check-input pl-3" value="valueSecond" v-model="check_Checked" @click="resetResult">
              </div>
            </div>
          </div>

          <div class="form-group mt-3">
            <div class="d-flex">
              <div class="wrap-input">
                <input type="number" class="form-control" v-model="valueThird">
              </div>

              <div class="wrap-input check">
                <input type="checkbox" class="form-check-input pl-3" value="valueThird" v-model="check_Checked" @click="resetResult">
              </div>
            </div>
          </div>

          <div class="errorMessage" v-show="errorMessage !== undefined">{{ errorMessage }}</div>

          <div class="d-flex">
            <div class="btn btn-primary mt-3 mx-auto" @click="checkBeforeOperate('penjumlahan')">+</div>
            <div class="btn btn-primary mt-3 mx-auto" @click="checkBeforeOperate('pengurangan')">-</div>
            <div class="btn btn-primary mt-3 mx-auto" @click="checkBeforeOperate('perkalian')">x</div>
            <div class="btn btn-primary mt-3 mx-auto" @click="checkBeforeOperate('pembagian')">/</div>
          </div>

          <hr>

          <div class="result" v-show="hasil !== undefined">
            <div class="result-content">Hasil</div>
            <div class="result-content">{{ hasil }}</div>
          </div>

          <div class="resetOperation" v-show="hasil !== undefined">
            <div class="btn btn-danger btn-sm" @click="resetResult">Reset</div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Home",
  data() {
    return {
      valueFirst: 10,
      valueSecond: 2,
      valueThird: 5,
      check_Checked: [],
      errorMessage: undefined,

      hasil: undefined,
    }
  },

  watch: {
    check_Checked() {

      if(this.check_Checked.length < 2) {
        this.errorMessage = "Silahkan checklist minimal 2 bilangan"
      } else {
        this.errorMessage = undefined
      }
      
      if(this.check_Checked.length == 0) {
        this.errorMessage = undefined
      }
    }
  },

  methods: {
    checkBeforeOperate(param) {
      this.hasil = undefined
      
      if(this.check_Checked.length == 0) {
        this.errorMessage = "Silahkan checklist inputan yang ingin dioperasikan terlebih dahulu."
      } else if (this.check_Checked.length < 2){
        this.errorMessage = "Silahkan checklist minimal 2 inputan"
      } else {
        if(param == "penjumlahan") {
          this.penjumlahan()
        } else if(param == "pengurangan") {
          this.pengurangan()
        } else if(param == "perkalian") {
          this.perkalian()
        } else if(param == "pembagian") {
          this.pembagian()
        }
      }
    },
    
    penjumlahan() {
      let action
      const includeFirst = this.check_Checked.includes("valueFirst")
      const includeSecond = this.check_Checked.includes("valueSecond")
      const includeThird = this.check_Checked.includes("valueThird")
        
      if(includeFirst && includeSecond && includeThird) { //Jika Checklist ketiganya
        action = parseInt(this.valueFirst) + parseInt(this.valueSecond) + parseInt(this.valueThird)
        this.hasil = action
      } else if (includeSecond && includeThird) { //Jika Checklist kedua dan ketiga
        action = parseInt(this.valueSecond) + parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeThird) { //Jika Checklist pertama dan ketiga
        action = parseInt(this.valueFirst) + parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeSecond ) { //Jika Checklist pertama dan kedua
        action = parseInt(this.valueFirst) + parseInt(this.valueSecond)
        this.hasil = action
      }
    },

    pengurangan() {
      let action
      const includeFirst = this.check_Checked.includes("valueFirst")
      const includeSecond = this.check_Checked.includes("valueSecond")
      const includeThird = this.check_Checked.includes("valueThird")
        
      if(includeFirst && includeSecond && includeThird) { //Jika Checklist ketiganya
        action = parseInt(this.valueFirst) - parseInt(this.valueSecond) - parseInt(this.valueThird)
        this.hasil = action
      } else if (includeSecond && includeThird) { //Jika Checklist kedua dan ketiga
        action = parseInt(this.valueSecond) - parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeThird) { //Jika Checklist pertama dan ketiga
        action = parseInt(this.valueFirst) - parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeSecond ) { //Jika Checklist pertama dan kedua
        action = parseInt(this.valueFirst) - parseInt(this.valueSecond)
        this.hasil = action
      }
    },

    perkalian() {
      let action
      const includeFirst = this.check_Checked.includes("valueFirst")
      const includeSecond = this.check_Checked.includes("valueSecond")
      const includeThird = this.check_Checked.includes("valueThird")
        
      if(includeFirst && includeSecond && includeThird) { //Jika Checklist ketiganya
        action = parseInt(this.valueFirst) * parseInt(this.valueSecond) * parseInt(this.valueThird)
        this.hasil = action
      } else if (includeSecond && includeThird) { //Jika Checklist kedua dan ketiga
        action = parseInt(this.valueSecond) * parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeThird) { //Jika Checklist pertama dan ketiga
        action = parseInt(this.valueFirst) * parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeSecond ) { //Jika Checklist pertama dan kedua
        action = parseInt(this.valueFirst) * parseInt(this.valueSecond)
        this.hasil = action
      }
    },

    pembagian() {
      let action
      const includeFirst = this.check_Checked.includes("valueFirst")
      const includeSecond = this.check_Checked.includes("valueSecond")
      const includeThird = this.check_Checked.includes("valueThird")
        
      if(includeFirst && includeSecond && includeThird) { //Jika Checklist ketiganya
        action = parseInt(this.valueFirst) / parseInt(this.valueSecond) / parseInt(this.valueThird)
        this.hasil = action
      } else if (includeSecond && includeThird) { //Jika Checklist kedua dan ketiga
        action = parseInt(this.valueSecond) / parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeThird) { //Jika Checklist pertama dan ketiga
        action = parseInt(this.valueFirst) / parseInt(this.valueThird)
        this.hasil = action
      } else if (includeFirst && includeSecond ) { //Jika Checklist pertama dan kedua
        action = parseInt(this.valueFirst) / parseInt(this.valueSecond)
        this.hasil = action
      }
    },

    resetResult() {
      this.hasil= undefined
    }
  }
};
</script>

<style scoped>
.main-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #fff;
  box-shadow: 0 3px 20px 10px rgb(151 169 204 / 14%);
    -webkit-box-shadow: 0 3px 20px 10px rgb(151 169 204 / 14%);
    -moz-box-shadow: 0 3px 20px 10px rgb(151 169 204/14%);
    -o-box-shadow: 0 3px 20px 10px rgb(151 169 204/14%);
  padding: 30px 20px;
  border-radius: 8px;
  text-align: start;
  width: 18rem;
}

.wrap-input {
  margin: 5px;
}

.check {
  display: flex;
  align-items: center;
}

.errorMessage {
  font-size: 12px;
  color: red;
  margin: 5px 0px
}

.result {
  font-size: 18px;
  display: flex;
}

.result-content {
  flex-grow: 1;
}

.result-content:nth-child(2) {
  text-align: end;
}

.resetOperation {
  margin-top: 5px;
  display: flex;
  justify-content: center;
}
</style>
