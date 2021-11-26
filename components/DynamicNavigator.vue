<template>
  <div ref='container' class='container'>
    <div class='navigator' ref='navigator'>
      <img src = '../static/home.svg' class = 'navigator-icon'/>
    </div>
  </div>
</template>

<script>
// import interact from 'interactjs'

export default {
  name: "DynamicNavigator",
  data() {
    return {
      activated: false,
      itemsWidthHeight: 15,
      activeItems: [],
      homeIcon : true,
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

    // to take draggable, delete comments
    // const position = { x: 0, y: 0 }
    //
    // interact(this.$refs.navigator).draggable({
    //   modifiers: [
    //     interact.modifiers.restrict({
    //       restriction: 'self',
    //       endOnly: true
    //     })
    //   ],
    //   listeners: {
    //     // start (event) {
    //     //   console.log(event.type, event.target)
    //     // },
    //     move (event) {
    //       position.x += event.dx
    //       position.y += event.dy
    //
    //       event.target.style.transform =
    //         `translate(${position.x}px, ${position.y}px)`
    //     },
    //   }
    // })

    for (let elem of this.navigatorItems) {
      let navigatorItem = document.createElement('div')
      navigatorItem.className = 'navigator-item'
      let parentProps = this.$refs.navigator.getBoundingClientRect();

      navigatorItem.style.left = parentProps.x + 30 + 'px';
      navigatorItem.style.top = parentProps.y + 30 + 'px';

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
    moveItems(previousRects) {
      for (let i = 0; i < this.navigatorItems.length; i++) {
        let indentX, indentY, background;
        // switch (i) {
        //   case 0:
        //     indentX = 40;
        //     indentY = 0;
        //     background = '#FF66CC';
        //     break
        //   case 1:
        //     indentX = -40;
        //     indentY = 0;
        //     background = '#FF3366';
        //     break
        //   case 2:
        //     indentX = 0;
        //     indentY = 40;
        //     background = '#FFFF66';
        //     break
        //   case 3:
        //     indentX = 0;
        //     indentY = -40;
        //     background = '#006699';
        //     break
        //   case 4:
        //     indentX = 28;
        //     indentY = 28;
        //     background = '#006633';
        //     break
        //   case 5:
        //     indentX = -28;
        //     indentY = -28
        //     background = '#00CCFF';
        //     break
        //   case 6:
        //     indentX = 28;
        //     indentY = -28;
        //     background = '#990099';
        //     break
        //   case 7:
        //     indentX = -28;
        //     indentY = 28;
        //     background = '#FF6633';
        //     break
        //   default:
        //     break
        // }

        switch (i) {
          case 0:
            indentX = 90;
            indentY = 0;
            background = '#FF3366';
            break
          case 1:
            indentX = -90;
            indentY = 0;
            background = '#FF3366';
            break
          case 2:
            indentX = 0;
            indentY = 90;
            background = '#FF3366';
            break
          case 3:
            indentX = 0;
            indentY = -90;
            background = '#FF3366';
            break
          case 4:
            indentX = 63;
            indentY = 63;
            background = '#FF3366';
            break
          case 5:
            indentX = -63;
            indentY = -63
            background = '#FF3366';
            break
          case 6:
            indentX = 63;
            indentY = -63;
            background = '#00CCFF';
            break
          case 7:
            indentX = -63;
            indentY = 63;
            background = '#00CCFF';
            break
          default:
            break
        }

        let navigatorItem;
        navigatorItem = this.activeItems[i];
        navigatorItem.style.background = background
        navigatorItem.style.zIndex ='1'
        navigatorItem.style.transition = 'all .3s linear'

        let parentProps = this.$refs.navigator.getBoundingClientRect()
        if (previousRects !== parentProps && !this.activated) {
          navigatorItem.style.left = parentProps.x + 10 + 'px';
          navigatorItem.style.top = parentProps.y + 10 + 'px';
        }

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
          // elem.style.transition = 'all 0s linear'
          // let parentProps = this.$refs.navigator.getBoundingClientRect()
          //
          // elem.style.left = parentProps.x + 15 + 'px';
          // elem.style.top = parentProps.y + 15 + 'px';
        }
      }
    }
  },
}
</script>

<style src='../layouts/default.css'>
</style>

