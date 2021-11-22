<template>
  <div ref='container'>
    <div class='navigator' ref='navigator'></div>
  </div>
</template>

<script>
export default {
  name: "DynamicNavigator",
  data() {
    return {
      activateItems: false,
      itemsWidthHeight: 15,
      activeItems: [],
      isUsed : false,
      navigatorItems: [
        {
          name: 'Profile',
          path: '/profile'
        },
        {
          name: 'Home',
          path: '/'
        }
      ]
    }
  },
  methods: {
    moveItems() {
      // event.stopPropagation() // doesn`t work
      // event.stopImmediatePropagation() // the same case
      let indent;
      let navigator = this.$refs.navigator
      for (let i = 0; i < this.navigatorItems.length; i++) {
        let navigatorItem = document.createElement('div');
        navigatorItem.className = 'navigator-item';

        if (this.isUsed) {
          navigatorItem = this.activeItems[i]
          // console.log(this.activeItems)
        } else {
          navigator.appendChild(navigatorItem)
        }

        // let navigatorProps = navigator.getBoundingClientRect()

        switch (i) {
          case 0:
            indent = !this.activateItems ? 50 : 0;
            break
          case 1:
            indent = !this.activateItems ? -50 : 0;
            break
          default:
            console.error('IndexError')
            break
        }

        // navigatorItem.style.transition = 'all .3s linear';

        navigatorItem.style.transform = `translate(${indent}px, 0px)`;

        navigatorItem.style.left = indent + 'px'
        this.activeItems.push(navigatorItem)
      }
      this.isUsed = true;
      this.activateItems = !this.activateItems
    }
  },
  mounted() {
    this.$refs.navigator.onclick = () => {
        this.moveItems()
    }
  }
}
</script>

<style src='../layouts/default.css'>

</style>
