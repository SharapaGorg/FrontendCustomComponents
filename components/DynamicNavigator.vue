<template>
  <div ref='container' class='container mx-auto' style="margin-top : 35vh">
    <div class='navigator' ref='navigator'>
      <img src = '../static/home.svg' class = 'navigator-icon mx-auto'/>
    </div>
  </div>
</template>

<style scoped>

.navigator {
  height: 75px;
  width: 75px;
  background : #00FFFF;
  border-radius: 50%;
  transition : all .3s linear;
  z-index : 100;
  position : relative;
  border: 2px solid #FF3366;

}

.navigator:hover {
  box-shadow: 0 10px 15px #574D4D;
  transition : all .3s linear;
  cursor: pointer;
  border: 2px solid #FF3366;
}

.container {
  width : 75px;
  height : 75px;
}

.navigator-icon {
  width : 35px;
  height : 35px;
  position: relative;
  top : 18px;
  color : #FF3366 !important;
}

</style>

<script>

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
        navigatorItem.style.boxShadow = '0 3px 2px #574D4D';

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
          elem.style.boxShadow = ''
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


