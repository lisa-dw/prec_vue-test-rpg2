<template>
  <div id="app">

   <input type="text"/>
    <br />
    <input type="text"/>
    <br />
    <input type="text"/>
    <br />
    <input type="text"/>
    <br />


    {{ item }}
    <br/>

    {{ items }}    <!--   이렇게 중괄호를 2개를 사용하면 자바스크립트(script) 부분의 변수를 표시해준다.-->
    <br />

    <button @click="t">t</button>


  </div>
</template>



<script>

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
    t(){    // t라는 메소드            //
      this.item.title ='foo'         //this는 눈치껏 잘 넣어서 쓰자..!
      this.item.content="Hello"
      },
  },

}

</script>



<style>

</style>
