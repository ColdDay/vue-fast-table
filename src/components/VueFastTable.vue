<template>
    <div class="vue-fast-table" ref="table" v-bind:class="scrollDirection">
        <div class="table-head">
          <div class="module" style="width:3000px"
            v-bind:style="{ transform: 'translateX(' + scrollLeft + 'px)' }"  
            v-for="(item, index) in monthArray" v-bind:key="index">
            <table width="3000" cellspacing="0" cellpadding="0">
              <thead>
                <tr>
                  <td colspan="30">2018-01-23</td>
                </tr>
                <tr>
                  <td>1</td>
                  <td>2</td>
                  <td>3</td>
                  <td>4</td>
                  <td>5</td>
                  <td>6</td>
                  <td>7</td>
                  <td>8</td>
                  <td>9</td>
                  <td>10</td>
                  <td>11</td>
                  <td>12</td>
                  <td>13</td>
                  <td>14</td>
                  <td>15</td>
                  <td>16</td>
                  <td>17</td>
                  <td>18</td>
                  <td>19</td>
                  <td>20</td>
                  <td>21</td>
                  <td>22</td>
                  <td>23</td>
                  <td>24</td>
                  <td>25</td>
                  <td>26</td>
                  <td>27</td>
                  <td>28</td>
                  <td>29</td>
                  <td>30</td>
                </tr>
              </thead>
            </table>
          </div>
        </div>
        <div class="table-body" @scroll="tableScroll">
          <div class="module" 
            style="width:3000px"
            v-for="(item, index) in monthArray" v-bind:key="index">
            <table  width="3000" 
              v-if="Math.abs(index - curModule)  < 3"
              cellspacing="0" cellpadding="0">
              <thead>
                <tr v-for="(item, index) in projectArray" v-bind:key="index">
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
                  <td><input type="text"></td>
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
    methods: {
      tableScroll(e) {
        const scrollLeft = e.target.scrollLeft
        const scrollTop = e.target.scrollTop
        if (scrollLeft == this.scrollLeft) {
          this.scrollDirection = 'vertical'
        } else {
          this.scrollDirection = 'horizontal'
        }
        this.curModule = parseInt(scrollLeft/3000)
        this.scrollLeft = -scrollLeft
        this.scrollTop = -scrollTop
      }
    },
    mounted() {
      let arr = []
      let projectArray = []
      for(var i=0; i< 120; i++) {
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
