<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <TheInput      
      v-model="inputValue"
      @enter="addItem"
      @addValue="addItem"
    />
    <hr />
    <ul>
      <TheList
        :name="item.todo"
        :style="listItemStyle(index)"
        v-for="(item, index) in items"
        :key="item.id"
        @remove="removeItem(index)"
      />
    </ul>
  </div>
</template>

<script>
import TheList from "./components/TheList/TheList.vue";
import TheInput from "./components/TheInput/TheInput.vue";

export default {
  components: {
    TheList,
    TheInput,
  },
  data() {
    return {
      title: "СПИСОК ЗАМЕТОК",
      items: [],
      idx: 0,
      inputValue: "",
    };
  },
  methods: {    
    addItem() {
      const textInput = this.inputValue.split(' ').join('')
      if (textInput !== '')
      this.items.push({
        id: this.idx++,
        todo: this.inputValue,
      });
      this.inputValue = "";
    },

    removeItem(index) {
      this.items.splice(index, 1);
    },

    listItemStyle(index) {
      var style = {};
      if (this.items[index].todo.length <= 5) {
        (style.color = "blue"), (style.fontWeight = "bold");
      } else {
        (style.color = "green"), (style.fontWeight = "light");
      }
      return style;
    },
  },
};
</script>

<style>
body {
  background: rgb(182, 178, 178);
}

h1 {
  width: 500px;
  margin-left: 30px;
  padding-top: 50px;
  color: rgb(83, 83, 206);
}

.container {
  background: white;
  border-radius: 20px;
  padding-bottom: 20px;
}
</style>
