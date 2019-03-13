<template>
    <div class="vue-fast-table" ref="table" v-bind:class="scrollDirection">
        <div class="table-head">
          <div class="module"
            v-bind:style="{ transform: 'translateX(' + scrollLeft + 'px)' }"  
            v-for="(item, index) in monthArray" v-bind:key="index">
            <table cellspacing="0" cellpadding="0">
              <thead>
                <tr>
                  <td colspan="30">2018-01-23</td>
                </tr>
                <tr>
                  <td width="100" style="min-width:100px">1</td>
                  <td width="100" style="min-width:100px">2</td>
                  <td width="100" style="min-width:100px">3</td>
                  <td width="100" style="min-width:100px">4</td>
                  <td width="100" style="min-width:100px">5</td>
                  <td width="100" style="min-width:100px">6</td>
                  <td width="100" style="min-width:100px">7</td>
                  <td width="100" style="min-width:100px">8</td>
                  <td width="100" style="min-width:100px">9</td>
                  <td width="100" style="min-width:100px">10</td>
                  <td width="100" style="min-width:100px">11</td>
                  <td width="100" style="min-width:100px">12</td>
                  <td width="100" style="min-width:100px">13</td>
                  <td width="100" style="min-width:100px">14</td>
                  <td width="100" style="min-width:100px">15</td>
                  <td width="100" style="min-width:100px">16</td>
                  <td width="100" style="min-width:100px">17</td>
                  <td width="100" style="min-width:100px">18</td>
                  <td width="100" style="min-width:100px">19</td>
                  <td width="100" style="min-width:100px">20</td>
                  <td width="100" style="min-width:100px">21</td>
                  <td width="100" style="min-width:100px">22</td>
                  <td width="100" style="min-width:100px">23</td>
                  <td width="100" style="min-width:100px">24</td>
                  <td width="100" style="min-width:100px">25</td>
                  <td width="100" style="min-width:100px">26</td>
                  <td width="100" style="min-width:100px">27</td>
                  <td width="100" style="min-width:100px">28</td>
                  <td width="100" style="min-width:100px">29</td>
                  <td width="100" style="min-width:100px">30</td>
                </tr>
              </thead>
            </table>
          </div>
        </div>
        <div class="table-body" @scroll="tableScroll">
          <div class="module" 
            style="width:3000px"
            v-for="(item, index) in monthArray" v-bind:key="index">
            <table width="3000" 
              v-if="Math.abs(index - curModule)  < 10"
              cellspacing="0" cellpadding="0">
              <thead>
                <tr v-for="(item, index) in projectArray" v-bind:key="index">
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                  <td @click="clickTd"><input type="text" @blur="blurTd" style="display:none"></td>
                </tr>
              </thead>
            </table>
          </div>
        </div>
         <div class="table-fix-cloumns">
          <div class="module fix-left-top">
            <table width="100" cellspacing="0" cellpadding="0">
              <thead>
                <tr>
                  <td>2</td>
                </tr>
                <tr>
                  <td>2</td>
                </tr>
              </thead>
            </table>
          </div>
          <div class="module"  v-bind:style="{ transform: 'translateY(' + scrollTop + 'px)' }">
            <table width="100" cellspacing="0" cellpadding="0">
              <thead>
                <tr v-for="(item, index) in projectArray" v-bind:key="index">
                  <td>1</td>
                </tr>
              </thead>
            </table>
          </div>
        </div>
    </div>
</template>

<script>

  export default {
    name: "vueFastTable",
    components: {
        
    },
    props: {
      columns: Array,
      data: Array,
      options: Object
    },
    data() {
      return {
        scrollLeft: 0,
        scrollTop: 0,
        scrollDirection: '',
        monthArray: [],
        projectArray: [],
        curModule: 0
      }
    },
    beforeCreate() {

    },
    methods: {
      tableScroll(e) {
        // console.log(e.target.scrollLeft)
        // window.sp && clearTimeout(sp)
        // window.sp = setTimeout(()=>{
          const scrollLeft = e.target.scrollLeft
          // console.log(this.scrollLeft, scrollLeft)
          const scrollTop = e.target.scrollTop
          if (scrollLeft == this.scrollLeft) {
            this.scrollDirection = 'vertical'
          } else {
            this.scrollDirection = 'horizontal'
          }
          this.curModule = parseInt(scrollLeft/3000)
          this.scrollLeft = -scrollLeft
          this.scrollTop = -scrollTop
        // },100)
        
      },
      clickTd(e) {
        e.target.childNodes[0].style.display = 'block'
        setTimeout(()=>{
          e.target.childNodes[0].focus()
        },20)
        
      },
      blurTd(e) {
        e.target.style.display = 'none'
        
      },
      resizeHead() {
        const headModules = document.querySelectorAll('.table-head .module')
        for(let i=0; i<headModules.length; i++) {

        }
      }
    },
    mounted() {
      let arr = []
      let projectArray = []
      for(var i=0; i< 36; i++) {
        arr.push(1)
      }
      for(var i=0; i< 100; i++) {
        projectArray.push(1)
      }
      this.monthArray = arr
      this.projectArray = projectArray
    }
  }
</script>

<style lang="scss" scoped>

.vue-fast-table{
  overflow: hidden;
  position: relative;
  td{
    background: #fff;
    height: 24px;
  }
  &.vertical{
    .table-head{
      z-index: 1
    }
  }
  input{
    width: 50px;
    height: 16px;
    box-sizing: border-box;
  }
}
.table-head{
  position: relative;
  display: -webkit-box;
  margin-left: 100px;
  .module{
    td{
      width: 100px;
      text-align: center;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }
  }
}
.table-body{
  display: -webkit-box;
  overflow: auto;
  height: 200px;
  margin-left: 100px;
  .module{
    td{
      width: 100px;
      text-align: center;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }
  }
}
.table-fix-cloumns{
  position: absolute;
  top: 0;
  left: 0;
  width: 100px;
  padding-top: 48px;
  .module{
    td{
      width: 100px;
      text-align: center;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }
  }
  .fix-left-top{
    position: absolute;
    top: 0;
    left: 0;
    width: 100px;
    height: 40px;
    z-index: 1;
  }
}
input{
  // display: none;
}
</style>
