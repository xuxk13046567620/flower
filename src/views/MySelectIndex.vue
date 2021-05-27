<template>
  <div>
    <!-- <my-select :content='this.$route.params.list' @func='show'></my-select> -->
    <div class="selectList">
      <div class="selectItem" v-if="list.length > 0">
        <my-select :content="list" @func="show" />
      </div>
      <!-- <div class="selectItem" v-if="list1.length > 0">
        <my-select ref='selectList1' :content1="list1" @func1="show1" />
      </div> -->
      <div class="selectItem" v-if="list1.length > 0">
        <select-one :content="list1" @func1="show1" />
      </div>
      <div class="selectItem" v-if="list2.length > 0">
        <select-two :content="list2" @func2="show2" />
      </div>
      <div class="selectItem" v-if="list3.length > 0">
        <select-three :content="list3" @func3="show3" />
      </div>
      <div class="selectItem" v-if="list4.length > 0">
        <select-four :content="list4" @func4="show4" />
      </div>
      <div class="selectItem" v-if="list5.length > 0">
        <select-five :content="list5" @func5="show5" />
      </div>
      <div class="selectItem" v-if="list6.length > 0">
        <select-six :content="list6" @func6="show6" />
      </div>
      <div class="selectItem" v-if="list7.length > 0">
        <select-seven :content="list7" @func7="show7" />
      </div>
      <div class="selectItem" v-if="list8.length > 0">
        <select-eight :content="list8" @func8="show8" />
      </div>
      <!-- <div class="selectItem"  v-if="list1.length > 0">
        <my-select :content="list1" @func="show"></my-select>
      </div>
      <div class="selectItem"  v-if="list1.length > 0">
        <my-select-one :content="list1" @func="show"></my-select-one>
      </div>
      <div class="selectItem"  v-if="list1.length > 0">
        <my-select-two :content="list1" @func="show"></my-select-two>
      </div> -->
    </div>

    <div class="txtList" v-if="txtList.length > 0">
      <div class="txtItem" v-for="(item, index) in txtList" :key="index">
        <!-- image -->
        <div
          v-if="
            item.name.substring(item.name.length - 3, item.name.length) ==
              'png' ||
            item.name.substring(item.name.length - 3, item.name.length) == 'jpg'
          "
          :link="item.link"
        >
          <div class="bgImg">
            <!-- {{'@/'+item.name1}} -->
            <!-- <img src="../../static/f1/f2/f0/f0/f1.jpg" alt="" /> -->
            <img :src="item.absolutePath1" alt="" />
          </div>
          <div class="title">{{ item.name }}</div>
        </div>
        <!-- word -->
        <div
          v-if="
            item.name.substring(item.name.length - 3, item.name.length) == 'doc'
          "
          :link="item.link"
        >
          <div class="bgImg"><img src="../../static/word.png" alt="" /></div>
          <div class="title">{{ item.name }}</div>
        </div>
        <!-- pdf -->
        <div
          v-if="
            item.name.substring(item.name.length - 3, item.name.length) == 'pdf'
          "
          :link="item.link"
        >
          <div class="bgImg"><img src="../../static/pdf.png" alt="" /></div>
          <div class="title">{{ item.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MySelect from "@/components/Select";
import SelectOne from "@/components/SelectOne";
import SelectTwo from "@/components/SelectTwo";
import SelectThree from "@/components/SelectThree";
import SelectFour from "@/components/SelectFour";
import SelectFive from "@/components/SelectFive";
import SelectSix from "@/components/SelectSix";
import SelectSeven from "@/components/SelectSeven";
import SelectEight from "@/components/SelectEight";
export default {
  components: {
    MySelect,
    SelectOne,
    SelectTwo,
    SelectThree,
    SelectFour,
    SelectFive,
    SelectSix,
    SelectSeven,
    SelectEight,
  },
  data() {
    return {
      list: [],
      list1: [],
      list2: [],
      list3: [],
      list4: [],
      list5: [],
      list6: [],
      list7: [],
      list8: [],
      list9: [],
      txtList: [],
    };
  },
  created() {
    // console.log(this.$route);
    let list = [];
    let txtList = [];
    console.log(this.$route.params.list);
    this.$route.params.list.forEach(function (item, index) {
      console.log(item.name.length, index);
      console.log(item.name.substring(item.name.length - 4, item.name.length));
      var typeEnd = item.name.substring(item.name.length - 3, item.name.length);
      if (
        typeEnd != "doc" &&
        typeEnd != "png" &&
        typeEnd != "jpg" &&
        typeEnd != "pdf" &&
        typeEnd != "JPG"
      ) {
        list.push(item);
      } else {
        
        txtList.push(item);
      }
      //   if (item.type == 1) {
      //     list.push(item);
      //   } else {
      //     txtList.push(item);
      //   }
    });
    console.log(list, txtList);
    this.list = list;
    this.txtList = txtList;

    this.list1 = [];
    this.list2 = [];
    this.list3 = [];
    this.list4 = [];
    this.list5 = [];
    this.list6 = [];
    this.list7 = [];
    this.list8 = [];
    console.log(list, txtList);
  },
  methods: {
    show(obj) {
      console.log(obj);
      // this.list1=obj.list
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
        
          txtList.push(item);
        }
      });
      this.list1 = list;
      this.txtList = txtList;
      this.list2 = [];
      this.list3 = [];
      this.list4 = [];
      this.list5 = [];
      this.list6 = [];
      this.list7 = [];
      this.list8 = [];
    },
    show1(obj) {
      //   console.log(obj);
      //   this.list2 = obj.list;
      console.log(obj);
      // this.list1=obj.list
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);
        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          
          txtList.push(item);
        }
      });
      this.list2 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list3 = [];
      this.list4 = [];
      this.list5 = [];
      this.list6 = [];
      this.list7 = [];
      this.list8 = [];
    },
    show2(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list3 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list4 = [];
      this.list5 = [];
      this.list6 = [];
      this.list7 = [];
      this.list8 = [];
    },
    show3(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list4 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list5 = [];
      this.list6 = [];
      this.list7 = [];
      this.list8 = [];
    },
    show4(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list5 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list6 = [];
      this.list7 = [];
      this.list8 = [];
    },
    show5(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list6 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list7 = [];
      this.list8 = [];
    },
    show6(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list7 = list;
      this.txtList = txtList;
      console.log(this.txtList);
      this.list8 = [];
    },
    show7(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list8 = list;
      this.txtList = txtList;
      console.log(this.txtList);
    },
    show8(obj) {
      let list = [];
      let txtList = [];
      obj.list.forEach(function (item, index) {
        console.log(item, index);

        var typeEnd = item.name.substring(
          item.name.length - 3,
          item.name.length
        );
        if (
          typeEnd != "doc" &&
          typeEnd != "png" &&
          typeEnd != "jpg" &&
          typeEnd != "pdf" &&
          typeEnd != "JPG"
        ) {
          list.push(item);
        } else {
          txtList.push(item);
        }
      });
      this.list9 = list;
      this.txtList = txtList;
      console.log(this.txtList);
    },
  },
};
</script>

<style lang="scss" scoped>
.selectList {
  padding: 10px 2.5%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  .selectItem {
    width: 47%;
    height: 50px;
    margin-bottom: 15px;
  }
}
.txtList {
  margin-top: 20px;
  width: 100%;
  height: auto;
  display: flex;
  justify-content: inherit;
  flex-wrap: wrap;
  padding: 10px 0 0;
  box-sizing: border-box;
  .txtItem {
    width: 30%;
    height: 140px;
    margin-left: 2.5%;
    .bgImg {
      width: 100%;
      height: 90px;
      img {
        width: 100%;
        height: 90px;
        object-fit: cover;
      }
    }
    .title {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      line-height: 40px;
    }
  }
}
</style>
