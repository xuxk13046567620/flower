<template>
  <div>
    <div class="posirelative select-out-div">
      <select
        class="select m-wrap"
        name=""
        id=""
        v-model="couponSelected"
        @change="getCouponSelected($event)"
      >
        <option :value="index+1" v-for="(item, index) in content" :key="index">
          {{ item.name }}
        </option>
      </select>
      <span class="select-hide-span"><b class="select-show-b"></b></span>
    </div>
  </div>
</template>

<script>
    export default {
        name:'my-select',
        props:['content'],
        data(){
            return {
                couponSelected:null,
                contentList:[]
            }
        },
        created () {
            this.couponSelected=this.content[0].id||'';
        },
        methods: {
            getCouponSelected(event) {
                this.ProductActive = event.target.value; //获取option对应的value值
                let content=this.content
                for(var i in content){
                    //   console.log(content[i]);
                    let ProductActive= this.ProductActive
                    if(parseInt(i)+1==ProductActive){
                        console.log(content[i],1);
                        this.$emit('func5',content[i])
                        this.contentList=content[i].list
                        content[i].list.forEach(element => {
                            console.log(element);
                            var typeEnd = element.name.substring(
              element.name.length - 3,
              element.name.length
            );
            if (
              typeEnd != "doc" &&
              typeEnd != "png" &&
              typeEnd != "jpg" &&
              typeEnd != "pdf" &&
              typeEnd != "JPG"
            ) {
              this.contentList.push(element);
            }
                        });
                        console.log(this.contentList);
                    }
                }
            }
        },
    }
</script>

<style lang="scss" scoped>
.select {
  //
  -webkit-appearance: none; /*去除chrome浏览器的默认下拉图片*/
  -moz-appearance: none; /*去除Firefox浏览器的默认下拉图片*/
  width: 100%;
  height: 50px;
  border: none;
  outline: none;
  border-radius: 10px;
  padding: 0 10px;
  box-sizing: border-box;
  position: absolute;
  top: 0;
  left: 0;
  font-size: 16px;
  // background: url("替换的图片路径") no-repeat right center;
  // 	background-size: 10px  10px;/*图片大小*/
  // 	background-position: 98%;/*图片位置*/
  // font-size: 16px;
  //   width: 40%;
  //   height: 50px;
  //   line-height: 50px;
  //   display: flex;
  //   padding: 0 10px;
  //   justify-content: center;
  //   border-radius: 10px;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  //   background-color: #ffffff;
  //   background-image: none !important;
  //   filter: none !important;
  //   border: none;
  // //   border: 1px solid #e5e5e5;
  //   outline: none;
  // height: 25px !important;
  // line-height: 25px;
  //   option {
  //     width: 100%;
  //     height: 100%;
  //     line-height: 50rpx;
  //     height: auto;

  //   }
}
.select:hover {
  background: #99b7f0;
}
.posirelative {
  position: relative;
  width: 100%;
  height: 50px;
  line-height: 50px;
  border: 1px solid #e5e5e5;
  border-radius: 10px;
  
}
/*使用伪类给select添加自己想用的图标*/
.posirelative:after {
  content: "";
  width: 14px;
  height: 14px;
  background: url(../../static/down.png); //no-repeat center;
  background-size: cover;
  /*通过定位将图标放在合适的位置*/
  position: absolute;
  right: 7px;
  top: 18px;
  /*给自定义的图标实现点击下来功能*/
  pointer-events: none;
}
</style>