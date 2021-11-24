<template>
  <div ref='container' class='container'>
    <div class='navigator' ref='navigator'></div>
  </div>
</template>

<script>
export default {
  name: "DynamicNavigator",
  data() {
    return {
      activated: false,
      itemsWidthHeight: 15,
      activeItems: [],
      navigatorItems: [
        {
          name: 'Profile',
          path: '/profile'
        },
        {
          name: 'Home',
          path: '/'
        },
        {
          name: 'Services',
          path: '/services'
        },
        {
          name: 'Auth',
          path: '/auth'
        },
        {},
        {},
        {},
        {}
      ]
    }
  },
  mounted() {
    for (let elem of this.navigatorItems) {
      let navigatorItem = document.createElement('div')
      navigatorItem.className = 'navigator-item'
      let parentProps = this.$refs.navigator.getBoundingClientRect();

      navigatorItem.style.left = parentProps.x + 15 + 'px';
      navigatorItem.style.top = parentProps.y + 15 + 'px';

      navigatorItem.title = elem.name

      this.$refs.container.appendChild(navigatorItem);
      this.activeItems.push(navigatorItem)
    }

    this.$refs.navigator.onclick = () => {
      this.moveItems()
    }
  },
  methods: {
    moveItems() {
      for (let i = 0; i < this.navigatorItems.length; i++) {
        let indentX, indentY;
        switch (i) {
          case 0:
            indentX = 40;
            indentY = 0;
            break
          case 1:
            indentX = -40;
            indentY = 0;
            break
          case 2:
            indentX = 0;
            indentY = 40;
            break
          case 3:
            indentX = 0;
            indentY = -40;
            break
          case 4:
            indentX = 28;
            indentY = 28;
            break
          case 5:
            indentX = -28;
            indentY = -28
            break
          case 6:
            indentX = 28;
            indentY = -28;
            break
          case 7:
            indentX = -28;
            indentY = 28;
            break
          default:
            break
        }

        let navigatorItem;
        navigatorItem = this.activeItems[i];

        let parentProps = this.$refs.navigator.getBoundingClientRect()
        navigatorItem.style.left = parentProps.x + 15 + 'px';
        navigatorItem.style.top = parentProps.y + 15 + 'px';

        if (this.activated) {
          navigatorItem.style.transform = `translate(0px, 0px)`
        } else {
          navigatorItem.style.transform = `translate(${indentX}px, ${indentY}px)`
        }
      }
      this.activated = !this.activated
    }
  },
}
</script>

<style src='../layouts/default.css'>

</style>
