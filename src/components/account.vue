<template>
  <div>
    <h1>account list</h1>
    <b-table striped hover :items="accounts"  :fields="columns"  >

    </b-table>
<!--    <table>-->
<!--      <thead>-->
<!--      <tr>-->
<!--        <th v-for="column in columns"  v-bind:key="column.key" >-->
<!--          {{ column.name }}-->
<!--        </th>-->
<!--      </tr>-->
<!--      </thead>-->
<!--      <tbody>-->
<!--      <tr v-for="item in accounts" v-bind:key="item.id">-->
<!--        <td v-for="column in columns" v-bind:key="column.key">-->
<!--          {{ viewFields(item,column) }}-->
<!--        </td>-->
<!--      </tr>-->
<!--      </tbody>-->
<!--    </table>-->

  </div>
</template>

<script>
import accountColumns from "./accountColumns.json"
import axios from "axios"

export default {
  name: "Account",
  data(){
    return {
      account:null ,
      accounts: null,
      columns : accountColumns
    }
  },
  mounted(){
     axios
        .get('http://nuc10:38000/tpservice/account/type/wechat')
        .then(response => (this.accounts = response.data))
  },
  methods:{
    viewFields(item,column){
      let funcName=column.func
      const key=column.key
      if  (funcName==null) {
        return item[key]
      }else{
        let func=eval("this."+funcName)
        return func(item[key])
      }
    },
    showEnable(sign){
      if (sign) {
        return "启用"
      }else{
        return "禁用"
      }
    },
    showTickets(tickets){
      let show=""
      for (const i in tickets) {
        show+=i+";"
      }
      return show
    },
  }
}
</script>

<style scoped>

</style>