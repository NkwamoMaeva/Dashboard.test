<template>
  <div class="drawer-container">
    <v-btn
      :class="{ active: menus[index].is_active }"
      v-for="(menu, index) in menus"
      :key="index"
      class="menu-button"
      :ripple="false"
      @click="activateMenu(index)"
      width="48px"
      height="48px"
      tile
      text
      fab
    >
      <v-icon :color="menus[index].is_active ? 'white' : 'grey'">{{
        menu.icon
      }}</v-icon>
      <div class="arrow_box">
        <ul>
          <li>Add new</li>
          <li>All sales</li>
          <li>Report</li>
          <li>Add new</li>
        </ul>
      </div>
    </v-btn>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toggle_exclusive: undefined,
      menus: [
        {
          name: "Dashboard",
          icon: "mdi-tune-vertical",
          is_active: true,
          submenus: [
            {
              name: "Add new",
              link: "#",
            },
            {
              name: "All sales",
              link: "#",
            },
            {
              name: "Report",
              link: "#",
            },
            {
              name: "Tags",
              link: "#",
            },
          ],
        },
        {
          name: "Dashboard",
          icon: "mdi-cart-outline",
          is_active: false,
          submenus: [
            {
              name: "Add new",
              link: "#",
            },
            {
              name: "All sales",
              link: "#",
            },
            {
              name: "Report",
              link: "#",
            },
            {
              name: "Tags",
              link: "#",
            },
          ],
        },
        {
          name: "Cart",
          icon: "mdi-chart-line",
          is_active: false,
          submenus: [
            {
              name: "Add new",
              link: "#",
            },
            {
              name: "All sales",
              link: "#",
            },
            {
              name: "Report",
              link: "#",
            },
            {
              name: "Tags",
              link: "#",
            },
          ],
        },
        {
          name: "Chart",
          icon: "mdi-account-multiple-outline",
          is_active: false,
          submenus: [
            {
              name: "Add new",
              link: "#",
            },
            {
              name: "All sales",
              link: "#",
            },
            {
              name: "Report",
              link: "#",
            },
            {
              name: "Tags",
              link: "#",
            },
          ],
        },
        {
          name: "Settings",
          icon: "mdi-cog-outline",
          is_active: false,
          submenus: [
            {
              name: "Add new",
              link: "#",
            },
            {
              name: "All sales",
              link: "#",
            },
            {
              name: "Report",
              link: "#",
            },
            {
              name: "Tags",
              link: "#",
            },
          ],
        },
      ],
    };
  },
  methods: {
    activateMenu(index) {
      this.menus.forEach((e) => {
        e.is_active = false;
      });
      this.menus[index].is_active = true;
    },
  },
};
</script>

<style scoped lang="scss">
.drawer-container {
  top: 80px;
  left: 16px;
  width: 48px;
  display: flex;
  height: 500px;
  border-radius: 5px;
  position: fixed;
  flex-direction: column;
  background-color: white;
  box-shadow: 0px 0px 9px -7px #000000;

  .active {
    background-color: #138be7;
  }

  .menu-button:first-child {
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
  }
  .v-btn {
    &::before {
      transition: none;
    }
    &:focus::before {
      opacity: 0;
    }
    &:focus {
      outline: none;
    }
    &:hover {
      color: #138be7;
      &::before {
        opacity: 0.15;
      }
      .v-icon {
        color: #138be7 !important;
      }
      .arrow_box {
        visibility: visible;
      }
    }
    .arrow_box {
      position: absolute;
      left: 45px;
      top: -12px;
      width: 100px;
      background: #000;
      border: 1px solid #000;
      visibility: hidden;
      border-radius: 3px;
      text-align: start;
      text-transform: initial;
      color: white;
      font-size: 12px;
      border: none;
      &:hover {
        visibility: visible;
      }
      ul {
        padding: 0;
        margin: 5px 0 !important;
        li {
          list-style-type: none; /* Remove bullets */
          padding: 3px 8px;
          &:hover {
            background-color: #138be7;
          }
        }
      }
    &:after,
    &:before {
      right: 100%;
      top: 20%;
      border: solid transparent;
      content: "";
      height: 0;
      width: 0;
      position: absolute;
      pointer-events: none;
    }
    &:after {
      border-color: rgba(255, 255, 255, 0);
      border-top-color: #000000;
      border-top: 7px;
      margin-top: -7px;
    }
    &:before {
      border-color: rgba(255, 255, 255, 0);
      border-top-color: #000000;
      border-width: 4px;
      margin-top: -4px;
      transform: rotate(90deg);
    }
    }
    
  }
}

.drawer-container .active {
  &:hover {
    .v-icon {
      color: white !important;
    }
  }
}
</style>
