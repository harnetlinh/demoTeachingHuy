<template>
  <div class="body">
    <div class="wrap"> 
      <div class="header"></div>
      <div class="content">
          <fieldset>
            <legend>Add book:</legend>
            <label for="fname">Name:</label>
            <input type="text" id="fname" name="fname" v-model="book.name"><br><br>
            <label for="lname">Publisher:</label>
            <input type="text" id="lname" name="lname" v-model="book.publisher"><br><br>
            <label for="author">Author:</label>
            <input type="text" id="author" name="author" v-model="book.author"><br><br>
            <label for="datepublish">Birthday:</label>
            <input type="date" id="datepublish" name="datepublish" v-model="book.date"><br><br>
            <input type="submit"  @click="onCreate()">
          </fieldset>
          <fieldset>
            <legend>Delete book:</legend>
            <label for="fid">ID:</label>
            <input type="text" id="fid" name="fid" v-model="book.id"><br><br>
            <button  @click="onDelete()"> Delete </button>
          </fieldset>
          <fieldset>
            <legend>Update book:</legend>
            <label for="editID">Choose a car:</label>
            <select name="editID" id="editID" v-model="book.id">
              <option v-for="(item,index) in listBook" :key="index" :value="item.id">
                {{ item.id }}
              </option>
            </select> <br><br>
            <label for="fname">Name:</label>
            <input type="text" id="fname" name="fname" v-model="book.name"><br><br>
            <label for="lname">Publisher:</label>
            <input type="text" id="lname" name="lname" v-model="book.publisher"><br><br>
            <label for="author">Author:</label>
            <input type="text" id="author" name="author" v-model="book.author"><br><br>
            <label for="datepublish">Birthday:</label>
            <input type="date" id="datepublish" name="datepublish" v-model="book.date"><br><br>
            <input type="submit"  @click="onUpdate()">
          </fieldset>
      </div>
      <div class="sidebar">
        <ul id="example-1">
          <li v-for="(item,index) in listBook" :key="index">
            {{item.id}} - {{ item.name }} - {{ item.author}}
          </li>
        </ul>
      </div>
      <div class="footer"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
  },
  data(){
    return{
      listBook: [
        {
          id:0,
          name:'book 1',
          publisher:'Kim Dong',
          author:'Van Cao',
          date:'12/05/2004' //dd/mm/yyyy
        },
        {
          id:1,
          name:'book 2',
          publisher:'Future',
          author:'John',
          date:'12/05/2004' //dd/mm/yyyy
        },
      ],
      book: {
        id:0,
        name:'',
        publisher:'',
        author:'',
        date:''
      }
    }
  },
  methods:{
    onCreate(){
      this.listBook.push({
        id:this.listBook.length ,
        name: this.book.name,
        publisher: this.book.publisher,
        author: this.book.author,
        date: this.book.date
      })
    },
    onDelete(){
      const _this = this;
      this.listBook = this.listBook.filter(function(aBook){
        return aBook.id.toString() !== _this.book.id;
      })
    },
    onUpdate(){
      for( var i in this.listBook){
        if(this.listBook[i].id === this.book.id){
          this.listBook[i].name = this.book.name;
          this.listBook[i].publisher = this.book.publisher;
          this.listBook[i].author = this.book.author;
          this.listBook[i].date = this.book.date;
        }
      }
    }
  }
}
</script>

<style scoped>
.body{
  margin: 0;
  padding: 0;
}
.wrap{
  width: 100vw;
  margin: 0 auto;
}
.header{
  height: 150px;
  margin-bottom: 15px;
  background-color: aquamarine;
}
.content{
  width: calc(80% - 10px);
  height: 600px;
  background-color: white;
  float: right;
  border: 2px solid black;
  border-radius: 12px;
}
.sidebar{
  width: calc(20% - 4px);
  height: 600px;
  border: 2px solid black;
  border-radius: 12px;
  /* background-color: blue; */
  float: left;
}
.footer{
  height: 200px;
  margin-top: 15px;
  background-color: yellow;
  width: 100vw;
  float: left;
}
</style>
