<template>
  <div ref='container' class='container'>
    <div class='navigator' ref='navigator'></div>
  </div>
</template>

<script>
import interact from 'interactjs'

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
          path: '/'
        },
        {
          name: 'Home',
          path: '/'
        },
        {
          name: 'Services',
          path: '/'
        },
        {
          name: 'Auth',
          path: '/'
        },
        {
          name: 'Route1',
          path: '/'
        },
        {
          name: 'Route2',
          path: '/'
        },
        {
          name: 'Route3',
          path: '/'
        },
        {
          name: 'Test',
          path: '/test'
        }
      ]
    }
  },
  mounted() {

    const position = { x: 0, y: 0 }

    interact(this.$refs.navigator).draggable({
      modifiers: [
        interact.modifiers.restrict({
          restriction: 'self',
          endOnly: true
        })
      ],
      listeners: {
        // start (event) {
        //   console.log(event.type, event.target)
        // },
        move (event) {
          position.x += event.dx
          position.y += event.dy

          event.target.style.transform =
            `translate(${position.x}px, ${position.y}px)`
        },
      }
    })

    for (let elem of this.navigatorItems) {
      let navigatorItem = document.createElement('div')
      navigatorItem.className = 'navigator-item'
      let parentProps = this.$refs.navigator.getBoundingClientRect();

      navigatorItem.style.left = parentProps.x + 15 + 'px';
      navigatorItem.style.top = parentProps.y + 15 + 'px';

      navigatorItem.title = elem.name

      this.$refs.container.appendChild(navigatorItem);
      this.activeItems.push(navigatorItem)

      navigatorItem.onclick = () => {
        this.$router.push(elem.path)
      }
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
        navigatorItem.style.zIndex ='1'

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

      if (!this.activated) {
        for (let elem of this.activeItems) {
          elem.style.zIndex = '-1'
        }
      }
    }
  },
}
</script>

<style src='../layouts/default.css'>

</style>
