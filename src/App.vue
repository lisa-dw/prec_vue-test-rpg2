<template>
  <div id="app">

 <input type="text" v-model="item.content"/>     <!--  이 input에서 받은 값을 해당 페이지에 data 부분의 item.content 에 집어넣겠다.-->
    <br />
    <input type="text" v-model="item.title"/>
    <br />
    <input type="text"/>
    <br />
    <input type="text"/>
    <br />


    {{ item }}
    <br/>

    {{ items }}    <!--   이렇게 중괄호를 2개를 사용하면 자바스크립트(script) 부분의 변수를 표시해준다.-->
    <br />

    <button @click="readItems">items</button>
    <button @click="createItem">createItem</button>

  </div>
</template>



<script>
import axios from 'axios'

const URL = 'http://localhost:8080/api/foos'  // /api 앞 부분은 본인이 부여받은 local을 사용하면 됨.



export default {
  name: 'App',


  data(){           // 이 data 부분을 수정하면 브라우저의 화면이 바뀌게끔 하는 단계.
    return{                     // 이 안에 객체를 넣는다.  // 객체를 리턴한다는 그런.
      item:{        // 단수들  // 항목  / 객체
        content: '',
        title: '',  // 문자열
      },
      items: [],    // 복수     // 목록 / list들 / 배열   , 만약에 {} 로 만들면 객체로 변경된다.

    }
  },


  methods : {

    async readItems() {
     const res = await axios.get(URL)   // axios.get() : 서버에 뭔가를 요청하는 것. // axios.get(URL) : axios에 get 명령어로 URL을 요청하는 것.
                                        // 해당 URL에 있는 정보들을 가져와라.
                                        // axios에서 응답을 기다렸다가 받으니까 await를 써준다.
      console.log(res)
      //console.log(res.data)           // 해당 URL에서 data에 포함되는 것들을 불러와서 콘솔에 찍어라. (서버에 요청하는 것)
    },
                                        //  laravel-test-rqg2폴더의 app/Http/Controllers/Api/Foo/FoosController.php에
                                        //  public function index() 의 내용이 없으면 이 부분이 보이지 않음(실행이 안됨).
    //


    async createItem(){
        const res = axios.post(URL, {     //axios.post에 {}<-(객체)를 넣으면 서버에 올라간다.

          content: this.item.content,    // 키:값 - 키와 값의 이름이 다르면 이렇게 적어줘야 하지만, 같으면 그렇게 해주지 않아도 됨.
          title: this.item.title,

          //위의 사항을 줄인것
          //...this.item,   // 앞에 ...을 쓰면 객체가 배열에 자식들을 풀어서 놔준다.

        })                                 // => item에 입력된 값들을 서버로 보내주는 함수.
    }
                                           //  laravel-test-rqg2폴더의 app/Http/Controllers/Api/Foo/FoosController.php에
                                           //  public function store() 의 내용이 없으면 이 부분이 보이지 않음(실행이 안됨).


  },

  watch: {    // 관찰 하라는
    item: {    // item을 관찰해라.
      deep: true, // item 밑에 있는 것들까지(item 항목에 속하는 것들) 다 관찰하라는 의미. - 깊게 관찰해라.
      handler(){  // 관찰하다가 무언가가 변경 되었을때, 해당하는 것을 실행하라. (handler 함수의 이름은 정해져 있는 것)
        console.log(this.item)
      },
    },
            // ## watch에서 item에 변화가 있을 때, handler() 함수를 실행하라.

  },



}

</script>



<style>

</style>
