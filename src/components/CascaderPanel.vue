<template>
    <div class="cascader-panel" >
        <ul v-if="data && data.length">
            <li :class="[{isactive:currentIndex===index}]" v-for="(item,index) in data" :data="item" :key="item.id" @mouseenter="showChild(item,index)" ><p>{{item.label}}</p></li>
            <div @mouseenter="enterul()" style="height:100%;"></div>
        </ul>
        <cascader-panel v-if="childMenu && childMenu.length" :data="childMenu"></cascader-panel>
    </div>
</template>

<script>

export default {
  name: "CascaderPanel",
  props: {
    data: Array
  },
  data() {
    return {
      childMenu: [],
      currentIndex:-1,
    };
  },
  watch: {
    data() {
      this.childMenu= [];
      this.currentIndex= -1;
    }
  },
  methods: {
    showChild(item,index) {
        this.currentIndex=index;
        this.childMenu = item.children;
    },
    enterul(){
      this.currentIndex = -1;
      this.childMenu = [];
    }
  }
};
</script>

<style scoped>
.cascader-panel {
  display: flex;
  height: 100%;
}
.isactive{
  color: blue;
}
li{
  width: 120px;
  cursor: pointer;
}
</style>
