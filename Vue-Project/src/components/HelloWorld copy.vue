<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <div style="width:250px">
      <div>
        <ul>
          <li v-for="(item,index) in data" 
          style="height:30px;border:1px dashed #ccc;color:#ccc;cursor:pointer;text-align:center;line-height:30px;padding:0 16px;" 
          :key='index' :id='item.id' :class="[item.tag?choosedStyle:'']"
          @click="clickLi(item)">
              {{item.label}}888899
          </li>
        </ul>
        <i class="el-icon-delete" @click="changeAdd" v-show='showText'></i>
        <div v-show="showAdd">
        <el-input v-model="input" placeholder="请输入内容"></el-input>
        <el-button type="primary" @click="saveAdd">主要按钮</el-button>
        </div>
        
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      tag:1,
      showText:true,
      showAdd:false,
      input:'',
      itemData:{},
      choosedStyle:'choosedStyle',
      data:[
        {
          id:'1',
          label:'dbskads',
          tag:false
        },{
          id:'2',
          label:'hhhhhh',
          tag:false
        },{
          id:'3',
          label:'rrrrr',
          tag:false
        },{
          id:'4',
          label:'tttttt',
          tag:false
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  },
  methods: {
      changeAdd(){
        this.showAdd = true
        this.showText = false
      },
      saveAdd(){
        this.showAdd = false
        this.showText = true
        const obj = {
          id:this.data.length+1,
          label:this.input,
          tag:false
        }
        this.data.push(obj)
      },
      clickLi(item){
        this.itemData=item
        for(let i in this.data){
          if(this.data[i].id == item.id){
            this.data[i].tag=true
          }else{
            this.data[i].tag=false
          }
        }

      },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      
      handleNodeClick(data,a,b) {
        console.log(data);
        console.log(a);
        
        
        this.getTag(a)
        console.log(this.tag,'8888888888888')
        if(this.tag==3){
          let id3 = a.id
          let id2 = a.parent.id
          let id1 = a.parent.parent.id
          console.log(id3,3)
          console.log(id2,2)
          console.log(id1,1)
        }
        this.tag = 1


        let i = 'aa-bb-cc'
        console.log(i.split('-'))
        if(i.split('-').length==3){
            console.log('yyyyyyyyyyyyy')
          }else{
            console.log('wangwenxuan')
          }
      },
      getTag(data){
        if(data.parent.id != false){
           this.tag++ 
           this.getTag(data.parent)
        }
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
.choosedStyle{
  color:blue!important;
  border-color:blue!important
}
</style>
