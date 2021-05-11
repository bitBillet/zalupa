<template>
  <div class="note_list">
    <div class="note" v-for="(note, index) in notes" :key="index">
      <div class="note_header">
        <p :hidden="note.isEdit">{{ note.title }}
          <span style="margin-left: 20px; color: aqua; cursor: default"
                @click="editTitle(note)"
          >Edit</span>
        </p>

        <input :hidden="!note.isEdit" type="text" :value="note.title" @keydown="save(note, $event)">
        <p @click="removeNote(index)" style="cursor: pointer">X</p>
      </div>
      <div class="note_body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Notes',
  props: {
    notes: {
      type: Array,
      require: true
    }
  },
  data() {
    return {
      isEdit: false
    }
  },
  methods: {
    removeNote(i) {
      console.log(`Removed note ${i}`)
      this.$emit('remove', i)
    },
    editTitle(note) {
      note.isEdit = true
    },
    save(note, event) {
      console.log(event)
      if (event.key === 'Enter') {
        note.title = event.target.value
        note.isEdit = false
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
