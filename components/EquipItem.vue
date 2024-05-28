<template>
   <div class="equip-item" :style="{
    borderColor: color,
    color: color
   }">
    <img :src="icon" alt=""  class="icon" :style="{
      borderColor: color
    }">
    <div class="equip-item-info">
      <div class="info">
        <text>{{ level }}</text>
        <text>{{ colorStr }}</text>
      </div>
      <div class="name">{{ name }}</div>
    </div>
   </div>
</template>
<script>

const COLOR_TYPE = [
  {
    "iColorId": 0,
    "sColor": "普通",
    "sColorCode": "#ffffff"
  },
  {
    "iColorId": 1,
    "sColor": "高级",
    "sColorCode": "#006df5"
  },
  {
    "iColorId": 2,
    "sColor": "稀有",
    "sColorCode": "#b36bff"
  },
  {
    "iColorId": 3,
    "sColor": "神器",
    "sColorCode": "#ff00ff"
  },
  {
    "iColorId": 5,
    "sColor": "远古",
    "sColorCode": "#ff0000"
  },
  {
    "iColorId": 4,
    "sColor": "史诗",
    "sColorCode": "#ffbb01"
  }
]

export default {
   name: 'equip-item',
   props: {
     item: {
       type: Object,
       default: () => ({})
     }
   },
   data() {
     return {
       
     }
   },
   computed: {
     level () {
       return `${this.item.iLevelLv}级`
     },
     icon () {
       return this.item.icon
     },
     name () {
       return this.item.szName
     },
     color () {
        const tmp = COLOR_TYPE.find((item) => {
          return item.iColorId === this.item.iColorId
        })
        console.log(`ny----tmp: `, tmp)
        return tmp?.sColorCode
     },
     colorStr () {
       return this.item.szColor
     },
     
   },
   watch: {
     
   },
   mounted() {
     
   },
   methods: {
     
   }
};
</script>
<style lang='scss' scoped>
.equip-item {
  box-sizing: border-box;
  background-color: var(--black);
  font-size: 14px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 4px;
  overflow: hidden;

  .icon {
    box-sizing: border-box;
    border-radius: 4px;
    border: 2px solid transparent;
    width: 58px;
    height: 58px;
  }

  .equip-item-info {
    box-sizing: border-box;
    padding: 4px 10px;
    height: 58px;
    flex: 1;
  }

  .info {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  
  .name {
    margin-top: 10px;
  }
}
</style>