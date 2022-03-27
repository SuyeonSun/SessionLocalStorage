<template>
<div>
  <button @click="saveSession">세션 스토리지 저장</button>
  <button @click="getSession">세션 스토리지 가져오기</button>
</div>

</template>
<script>
export default {
  methods: {
    saveSession() {
      // 문자열로 set 하는 경우
      // sessionStorage.setItem('name','ironman')

      // 객체, 배열 등을 넣게 되는 경우 객체를 바로 저장 하게 되면 [object Object]로 저장된다. (Local Storage로 동일)
      // storage에는 반드시 문자열만 저장 가능하며 다른 타입을 저장하기 위해서는 문자열로 변환 후 저장 가능하다.
      const payload = {'name':'ironman'};
      sessionStorage.setItem('name', JSON.stringify(payload))
      // JSON.parse()로 원래의 타입으로 복구 가능
        },

      getSession() {
        // 문자열인 경우는 단순히 아래와 같이 가져오면 된다.
        // const data = sessionStorage.getItem("name");
        
        // 객체인 경우는 아래처럼 원래 타입으로 parse 해준다.
        const data = JSON.parse(sessionStorage.getItem("name"));
        console.log("data=========>",data)
    },
  },
}
</script>
