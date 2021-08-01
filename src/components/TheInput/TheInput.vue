<template>
  <div class="form-control">
    <input type="text" :placeholder="placeholderStr" v-model="inputVal" @keypress.enter="$emit('enter')"/>
    <button class="btn add" @click="$emit('addValue')">ДОБАВИТЬ</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      placeholderStr: "Введите название заметки",
    };
  },
  props: {
    modelValue: {
      type: String,
    },
  },
  emits: ["enter", "addValue"],
  //   render() {
  //     return createElement("input", {
  //       modelValue: this.modelValue,
  //       "onUpdate:modelValue": (event) => this.$emit("update:modelValue", event.target.value),
  //     });
  //   },
  computed: {
    inputVal: {
      get() {
        return this.modelValue;
      },
      set(val) {
        this.$emit("update:modelValue", val);
      },
    },
  },
};
</script>

<style  scoped>
input {
  font-size: 20px;
  margin-bottom: 10px;
  width: 800px;
  padding: 15px 0px 15px 20px;
  border: 2px solid rgb(20, 104, 20);
  background: #f6f6f6;
}

.form-control {
  padding: 5px;
  margin-left: 20px;
  margin-top: 50px;
}

.btn {
margin-left: 20px;
  margin-right: 20px; 
  border-radius: 25px;
  width: 150px;
  padding: 15px;
  font-family: "Times New Roman", Times, serif;
  font-weight: bolder;
  font-size: 15px;
  margin-top: 5px;
  margin-bottom: 15px;
}

.add {
  background: white;
  color: rgb(20, 104, 20);
  border: 2px solid rgb(20, 104, 20);
}
</style>