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
         <!-- v-if="Math.abs(index - curModule)  < 1" -->
        <div class="table-body" @scroll="tableScroll">
          <div class="module" 
            style="width:3000px;height: 160px"
            v-for="(item, index) in monthData" v-bind:key="index">
            <table width="3000" 
              cellspacing="0" cellpadding="0">
              <thead>
                <tr v-for="(p_item, p_index) in projectData" v-bind:key="p_index">
                  <td @click="clickTd" v-for="(d_item, d_index) in item.days" v-bind:key="d_index">
                   <!-- {{p_index +'====' + item.month + '===' + d_item}} -->
                    {{(originProjectData[p_index][''+item.month][''+d_item]['last'])}}
                  </td>
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
        originProjectData: [
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
          {
            '2018-12': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-01': {
              '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-02': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            },
            '2019-03': {
             '01': {
                last: 2,
                max: 1
              },
              '02': {
                last: 2,
                max: 1
              },
              '03': {
                last: 2,
                max: 1
              },
              '04': {
                last: 2,
                max: 1
              },
              '05': {
                last: 2,
                max: 1
              },
              '06': {
                last: 2,
                max: 1
              },
              '07': {
                last: 2,
                max: 1
              },
              '08': {
                last: 2,
                max: 1
              },
              '09': {
                last: 2,
                max: 1
              },
              '10': {
                last: 2,
                max: 1
              },
              '11': {
                last: 2,
                max: 1
              },
              '12': {
                last: 2,
                max: 1
              },
              '13': {
                last: 2,
                max: 1
              },
              '14': {
                last: 2,
                max: 1
              },
              '15': {
                last: 2,
                max: 1
              },
              '16': {
                last: 2,
                max: 1
              },
              '17': {
                last: 2,
                max: 1
              },
              '18': {
                last: 2,
                max: 1
              },
              '19': {
                last: 2,
                max: 1
              },
              '20': {
                last: 2,
                max: 1
              },
              '21': {
                last: 2,
                max: 1
              },
              '22': {
                last: 2,
                max: 1
              },
              '23': {
                last: 2,
                max: 1
              },
              '24': {
                last: 2,
                max: 1
              },
              '25': {
                last: 2,
                max: 1
              },
              '26': {
                last: 2,
                max: 1
              },
              '27': {
                last: 2,
                max: 1
              },
              '28': {
                last: 2,
                max: 1
              },
              '29': {
                last: 2,
                max: 1
              },
              '30': {
                last: 2,
                max: 1
              }
            }
          },
        ],
        projectData: [
          {
            name: '项目A',
            type: 1
          },
          {
            name: '项目B',
            type: 1
          },
          {
            name: '项目C',
            type: 1
          },
          {
            name: '项目D',
            type: 1
          },
          {
            name: '项目E',
            type: 1
          },
          {
            name: '项目F',
            type: 1
          }
        ],
        monthData: [
          {
            month: '2018-12',
            days: [
              '01',
              '02',
              '03',
              '04',
              '05',
              '06',
              '07',
              '08',
              '09',
              '10',
              '11',
              '12',
              '13',
              '14',
              '15',
              '16',
              '17',
              '18',
              '19',
              '20',
              '21',
              '22',
              '23',
              '24',
              '25',
              '26',
              '27',
              '28',
              '29',
              '30'
            ]
          },
          {
            month: '2019-01',
            days: [
              '01',
              '02',
              '03',
              '04',
              '05',
              '06',
              '07',
              '08',
              '09',
              '10',
              '11',
              '12',
              '13',
              '14',
              '15',
              '16',
              '17',
              '18',
              '19',
              '20',
              '21',
              '22',
              '23',
              '24',
              '25',
              '26',
              '27',
              '28',
              '29',
              '30'
            ]
          },
          {
            month: '2019-02',
            days: [
              '01',
              '02',
              '03',
              '04',
              '05',
              '06',
              '07',
              '08',
              '09',
              '10',
              '11',
              '12',
              '13',
              '14',
              '15',
              '16',
              '17',
              '18',
              '19',
              '20',
              '21',
              '22',
              '23',
              '24',
              '25',
              '26',
              '27',
              '28',
              '29',
              '30'
            ]
          },
          {
            month: '2019-03',
            days: [
              '01',
              '02',
              '03',
              '04',
              '05',
              '06',
              '07',
              '08',
              '09',
              '10',
              '11',
              '12',
              '13',
              '14',
              '15',
              '16',
              '17',
              '18',
              '19',
              '20',
              '21',
              '22',
              '23',
              '24',
              '25',
              '26',
              '27',
              '28',
              '29',
              '30'
            ]
          }
        ]
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
