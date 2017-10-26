<template></template>
<script>
  export default {
      name:'util',
      methods:{
          getYear(nowDate){
            return nowDate.getFullYear();
          },

          getMonth(nowDate){
            return (nowDate.getMonth() + 1);
          },

           getDay(nowDate){
             return nowDate.getDate();
           },

           getHour(nowDate){
             return nowDate.getHours()+1;
           },

            getMinutes(nowDate){
              return  nowDate.getMinutes()+1;
            },

           getMM(nowDate){
               return  this.leftPad(this.getMonth(nowDate));
           },

           getDD(nowDate){
               return this.leftPad(this.getDay(nowDate));
           },

          getHH(nowDate){
               return this.leftPad(this.getHour(nowDate));
          },

          getmm(nowDate){
              return this.leftPad(this.getMinutes(nowDate));
          },


          leftPad(param){
              return param < 10 ?"0"+param :param;
          }
      },
      change01 (param){
        let p = parseInt(param);
        return 1^p;
      },
      getMMDD (){
             let nowDate = new Date();
             console.log(this);
              return this.methods.getMM(nowDate) + "/" + this.methods.getDD(nowDate);
      },

      getMMDDbyMil (param){
          let date = new Date(param);
          return this.methods.getMM(date) + "/" + this.methods.getDD(date);
      },

      getMMDDHHmmbyMil(param){
        let date = new Date(param);
        return this.methods.getMM(date) + "/" + this.methods.getDD(date) + " " + this.methods.getHour(date)+ ":"+this.methods.getMinutes(date);
      }


  }
</script>
<style></style>
