<template>
  <li>
    {{ name
    }}<button class="btn delete" @click="$emit('remove')">DELETE</button>
  </li>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: "Здесь не хватает имени",
    },
  },
  emits: ["remove"],
};
</script>

<style scoped>
li {
  list-style-type: none;
  color: black;
  text-transform: uppercase;
  display: flex;
  justify-content: space-between;
  align-items: center;
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

.delete {
  background: red;
  color: white;
  border: 2px solid darkred;
}
</style>