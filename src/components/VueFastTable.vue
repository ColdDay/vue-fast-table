<template>
    <div class="vue-fast-table" ref="table" v-bind:class="scrollDirection">
        <div class="table-head">
          <div class="module"
            v-bind:style="{ transform: 'translateX(' + scrollLeft + 'px)' }"  
            v-for="(item, index) in monthData" v-bind:key="index">
            <table cellspacing="0" cellpadding="0">
              <thead>
                <tr>
                  <td colspan="30">{{item.month}}</td>
                </tr>
                <tr>
                  <td width="100" 
                    v-for="(d_item, d_index) in item.days" v-bind:key="d_index"
                    style="min-width:100px">{{d_item}}</td>
                  
                </tr>
              </thead>
            </table>
          </div>
        </div>
        <div class="table-body" @scroll="tableScroll" style="height: 300px">
          <div class="module" 
            style="width:3000px;"
            v-for="(item, index) in monthData" v-bind:key="index">
            <div class="content" 
              v-if="Math.abs(index - curModule)  < 3">
              <div class="row"
                style="height:30px"
                v-for="(p_item, p_index) in projectData" 
                v-bind:key="p_index">
                <table width="3000"
                  v-if="Math.abs(p_index - curRow)  < 20"
                  cellspacing="0" cellpadding="0">
                  <tbody>
                    <tr>
                      <td @click="clickTd" v-for="(d_item, d_index) in item.days" v-bind:key="d_index">
                        {{(originProjectData[p_index][''+item.month][''+d_item]['last'])}}
                      <!-- <input/> -->
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              

            </div>
            
          </div>
        </div>
         <div class="table-fix-cloumns">
          <div class="module fix-left-top">
            <table width="100" cellspacing="0" cellpadding="0">
              <thead>
                <tr>
                  <td>位置</td>
                </tr>
                <tr>
                  <td>position</td>
                </tr>
              </thead>
            </table>
          </div>
          <div class="module"  v-bind:style="{ transform: 'translateY(' + scrollTop + 'px)' }">
            <table width="100" cellspacing="0" cellpadding="0">
              <thead>
                <tr v-for="(item, index) in projectData" v-bind:key="index">
                  <td>{{item.name}}</td>
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
        curModule: 0,
        curRow: 0,
        originProjectData: [],
        projectData: [],
        monthData: [],
        options: {
          rowHeight: 30,
          colWidth: 100
        }
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
          this.curRow = parseInt(scrollTop/30)
          this.scrollLeft = -scrollLeft
          this.scrollTop = -scrollTop
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
      initData(monthNum, projectNum) {

        let monthData = [];
        let projectData = [];
        let originProjectData = []
        for(let i = 0;i < monthNum; i++) {
          monthData.push({
            month: '2019-0' + (i+1),
            days: ['01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11', '12', '13', '14', '15', '16', '17','18', '19', '20', '21', '22', '23', '24', '25', '26', '27', '28', '29', '30']
          })
        }
        for(let i = 0; i < projectNum; i++) {
          projectData.push({name: '项目' + (i+1), type: 1});
          let data = {};
          monthData.forEach((m_item)=>{
            let days = {};
            m_item.days.forEach((d_item)=>{
              days[d_item] = {last: 2, max: 1}
            })
            data[m_item.month] = days;
          })
          originProjectData.push(data);
        }
        this.monthData = monthData;
        this.projectData = projectData;
        this.originProjectData = originProjectData;
      }
    },
    mounted() {
      var startDate = new Date().getTime()
      this.initData(100, 100)
      console.log('计算耗时' + new Date().getTime() - startDate)
    }
  }
</script>

<style lang="scss" scoped>

.vue-fast-table{
  overflow: hidden;
  position: relative;
  td{
    background: #fff;
    height: 30px;
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
  height: 160px;
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
  padding-top: 60px;
  .module{
    td{
      width: 100px;
      height: 30px;
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
