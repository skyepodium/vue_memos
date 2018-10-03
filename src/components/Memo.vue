<template>
  <div id = "container">

    <div id="title">
      메모장
    </div>

      <div id="memo_group">
        <label for="add_memo">
          <input id="add_memo" placeholder="메모 입력하세요"
                 v-model="name"
                 v-on:keyup.enter="create_memo(name)" type="text">
        </label>
        <button id="add_btn" @click = "create_memo(name)">추가</button>
        <div id="cc"></div>

      </div>

    <div id="memos" v-if="this.memos.length > 0">
      <li class="memo" v-for="(memo, index) in memos">
        <div class="memo_name"> {{memo.name }} </div>
        <button class="memo_btn" @click = "delete_memo(index)"> 삭제 </button>
      </li>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'Memo',
    data () {
      return {
        name: null,
        memos: [{name: '청소'}, {name: '놀기'}, {name: 'Vue'}],
      }
    },
    methods:{
      create_memo(name){
        if(name != null) {
          this.memos.push({name:name});
          this.name = null;
        }
      },
      delete_memo(index){
        console.log(index);
        this.memos.splice(index, 1);
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *{
    padding:0;
    margin:0;
  }

  #container{
    width:calc(100% - 40px);
    border:1px solid #ececec;
    margin-left:auto;
    margin-right:auto;
    padding-bottom:30px;
  }

  @media screen and (min-width:700px) {
    #container {
      width: 600px;
    }
  }

  #title{
    width:calc(100% - 30px);
    font-size:35px;
    font-weight:bold;
    margin: 30px auto 20px;
  }

  #memo_group{
    width:calc(100% - 30px);
    height:50px;
    margin-left:auto;
    margin-right:auto;
    border:1px solid #ececec;
    box-sizing: border-box;
  }
  #add_memo{
    width:calc(100% - 70px);
    height:100%;
    margin-left:20px;
    border:none;
    float:left;
    font-size:20px;
  }

  #add_btn{
    width:50px;
    height:100%;
    padding: 0;
    border:none;
    background: none;
    font-size:16px;
  }
  #add_btn:active{
    background-color:#ececec;
  }

  #memos{
    margin-top:30px;
    width:calc(100% - 30px);
    margin-left:auto;
    margin-right:auto;
    border-bottom:1px solid #ececec;
  }
  .memo{
    list-style: none;
    width:100%;
    height:50px;
    margin-left:auto;
    margin-right:auto;
    border:1px solid #ececec;
    box-sizing: border-box;
    border-bottom:none;
  }

  .memo_name{
    width:calc(100% - 100px);
    height:100%;
    float:left;
    line-height:50px;
    color:black;
    font-size:18px;
    text-align: left;
    margin-left:20px;
  }
  .memo_btn{
    width:60px;
    height:100%;
    color:cornflowerblue;
    line-height:50px;
    padding: 0;
    border: none;
    background: none;
  }
  .memo_btn:active{
    background-color:#ececec;
  }


</style>
