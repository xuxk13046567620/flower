<template>
  <div>
    <!-- 21312121321312 -->
    <!-- <my-select :content="list"></my-select> -->
    <div class="ulList">
      <ul>
        <li
          v-for="(item, index) in list"
          :key="index"
          @click="jumpThis(index)"
        >
          {{ item.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// import MySelect from "@/components/Select";
    // console.log(appData)
    export default {
        data() {
            return{
                list:[],
                couponSelected:null,
            }
        },
        // components: {MySelect},
        created () {
            let list = require('../assets/flowers.json');
            console.log(list);
            this.list=list
            this.couponSelected=list[0].name1
            // console.log(list);
            console.log(this.list, this.couponSelected);
        },
        methods: {
           jumpThis(e){
               console.log(e);
               console.log(this.list,this.list[e].list);
            //    this.$router.push({
            //         path: '/myselectindex',
            //         params: {id:e},
            //     })
                this.$router.push({
                    name:'MySelectIndex',
                    params: {
                        id:e,
                        list:this.list[e].list
                        },
                })
           }
        },
    }
</script>

<style lang="scss" scoped>
.ulList {
  margin: 50px auto;
  //   display: flex;
  //   justify-content: center;
  width: 100%;
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
    width: 90%;
    margin: 0 auto;
    li {
      line-height: 50px;
      width: 100%;
      // margin: 0 auto;
      border: 1px solid #e5e5e5;
      text-overflow: ellipsis;
      white-space: nowrap;
      overflow: hidden;
      padding: 0 10px;
      box-sizing: border-box;
      margin: 0 0 -1px -1px;
    }
  }
}
</style>