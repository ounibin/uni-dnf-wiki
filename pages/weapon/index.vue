<template>
  <view class="">
    新的页面
  </view>
</template>

<script>
import EquipItem from '/components/EquipItem.vue'
import posList from '/data/pos-type.json'
import equipData from '/data/equip.json'

export default {
  components: {
    EquipItem
  },
  data() {
    return {
      posList,
      posIndex: 0,
      leftIndex: 0,
      leftSubIndex: 0,
      equipList:[]
    }
  },
  computed: {
    leftList() {
      return this.posList[this.posIndex]?.sSonIds||[]
    },
    leftSubList() {
      return this.leftList[this.leftIndex]?.sSonIds||[]
    }
  },
  watch:{
    // posIndex (val) {
    //   this.findEquip(this.posIndex, this.leftIndex, this.leftSubIndex)
    // },
    // leftIndex (val) {
    //   this.findEquip(this.posIndex, this.leftIndex, this.leftSubIndex)
    // },
    // leftSubIndex (val) {
    //   this.findEquip(this.posIndex, this.leftIndex, this.leftSubIndex)
    // },
  },
  methods: {
    clickEquType(i) {
      if(i===this.posIndex)return
      this.posIndex = i
      this.leftIndex = 0
      this.findEquip(this.leftSubList[this.leftSubIndex]?.iTypeSon2Id)
    },
    clickLeft(i){
      if(i===this.leftIndex)return
      this.leftIndex = i
      this.leftSubIndex = 0
      this.findEquip(this.leftSubList[this.leftSubIndex]?.iTypeSon2Id)
    },
    clickSubLeft(e){
      const doms = document.querySelectorAll('.sub-left-btn')
      const i = Number(e.target.dataset.index)
      if(i===this.leftSubIndex)return
      this.leftSubIndex = i
      doms.forEach((item) => {
        item.style.backgroundColor='transparent'
      })
      e.target.style.backgroundColor='#ff00cc'
      this.findEquip(this.leftSubList[this.leftSubIndex]?.iTypeSon2Id)
    },
    findEquip(id){
      if(!id) {
        this.equipList=[]
        return 
      }
      const list = equipData.filter((item) => {
        return item.iTypeSon3Id.includes(`${id}`)
      })
      this.equipList=list
    },
    clickEquipItem(i){
      const item = this.equipList[i]
      console.log(`ny----item.szName: `, item.szName)
    }
  }
}
</script>

<style lang="scss">
.top-bar {
  display: flex;
  flex-direction: row;

  .btn {
    width: 30px;
    line-height: 30px;
    flex: 1;
  }
}

.content-box {
  display: flex;
  
}

.left-list {
  // height: 100px;
  width: 93px;
  .btn {
    width: 93px;
    height: 30px;
    line-height: 30px;
  }
}

.sub-left-list {
  width: 100%;
  .sub-left-btn {
    width: 100%;
    height: 30px;
    line-height: 30px;
  }
  .sub-left-btn-active {
    background-color: #ff00cc;
  }
}

.right-list {
  padding: 10px;
  flex: 1;
  // display: grid;
  // display: grid;
  // grid-template-columns: 1fr 1fr 1fr 1fr;
  // gap: 10px;
  // justify-items: center; /* 水平居中所有网格项 */
  // align-items: start; /* 垂直顶部对齐所有网格项 */
  // justify-content: space-between; /* 网格容器内的水平间距 */
  // align-content: space-around; /* 网格容器内的垂直间距 */
  // .equip-item {
  //   width: 58px;
  //   height: 58px;
  //   border-radius: 4px;
  // }
}
</style>
