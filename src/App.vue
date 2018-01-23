<template>
  <div id="app">
    <div class="div" @mouseenter="showall()" @mouseleave="showaleave()">
      <button class="btn">主菜单</button>
      <div class="cascader" v-show="show">
        <cascader-panel :data="list"></cascader-panel>
      </div>
    </div>
    
    <p>111111111111111111111111111111111111111111111111111111111111111111111111</p>
  </div>
</template>

<script>
import CascaderPanel from "./components/CascaderPanel";

export default {
  components: {
    CascaderPanel
  },
  props: {
    data: Array,
  },
  data() {
        return {
            menuList: [
                {
                    label: "菜单一",
                    children: [
                        {
                            label: "二级菜单_1",
                            children: [
                                {
                                    label: "三级菜单_1",
                                    children: [
                                          {
                                              label: "四级菜单_1"
                                          }
                                      ]
                                }
                            ]
                        },
                        {
                            label: "二级菜单_2",
                            
                        }
                    ]
                },
                {
                    label: "菜单二",
                    children: [
                        {
                            label: "二级菜单",
                            children: [
                                {
                                    label: "三级菜单_1"
                                }
                            ]
                        }
                    ]
                }
            ],
            show:false,
            list:[]
        }
    },

  methods:{
    showall(){
    this.show=true;
    this.list=this.menuList;
    },
    showaleave(){
    this.show=false;
    this.list=[];
    },

    }
};

</script>

<style>
.cascader{
  position: absolute;
  height: 100%;
  background-color: #eee;
}
.btn,.div{
    height: 50px;
    width: 100px;
}
</style>
