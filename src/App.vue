<template>
  <div id="app">
    <div class="layout">
      <Layout>
        <Sider
          ref="side1"
          hide-trigger
          collapsible
          :collapsed-width="78"
          v-model="isCollapsed"
        >
          <Menu
            active-name="1-2"
            theme="dark"
            width="auto"
            :class="menuitemClasses"
          >
            <menu-item name="1-1">
              <Icon type="ios-navigate"></Icon>
              <span>Home</span>
            </menu-item>
            <menu-item name="1-2">
              <Icon type="ios-search"></Icon>
              <span>素材查找</span>
            </menu-item>
            <menu-item name="1-3">
              <Icon type="ios-settings"></Icon>
              <span>系统设置</span>
            </menu-item>
            <menu-item
              name="1-4"
              style="position: fixed;bottom: 10px;text-align: center;"
            >
              <Icon type="ios-person" size="32"></Icon>
            </menu-item>
          </Menu>
        </Sider>
        <Layout>
          <Header :style="{ padding: 0 }" class="layout-header-bar">
            <Icon
              @click.native="collapsedSider"
              :class="rotateIcon"
              :style="{ margin: '0 20px' }"
              type="md-menu"
              size="24"
            ></Icon>
          </Header>
          <Content
            :style="{
              margin: '20px',
              background: '#fff',
              minHeight: '860px',
              height: '100%'
            }"
          >
            <router-view/>
          </Content>
        </Layout>
      </Layout>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  props: {},
  data () {
    return {
      isCollapsed: false
    }
  },
  computed: {
    rotateIcon () {
      return ['menu-icon', this.isCollapsed ? 'rotate-icon' : '']
    },
    menuitemClasses () {
      return ['menu-item', this.isCollapsed ? 'collapsed-menu' : '']
    }
  },
  methods: {
    collapsedSider () {
      this.$refs.side1.toggleCollapse()
    }
  }
}
</script>
<style lang="scss" scoped>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    height: 100%;
  }

  .layout {
    border: 0px solid #d7dde4;
    background: #f4f7f9;
    position: relative;
    border-radius: 3px;
    overflow: hidden;
  }

  .layout-header-bar {
    background: #fff;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
  }

  .layout-logo-left {
    width: 89%;
    height: 29px;
    background: #4b6270;
    border-radius: 2px;
    margin: 14px auto;
  }

  .menu-icon {
    transition: all -1.3s;
  }

  .rotate-icon {
    transform: rotate(-91deg);
  }

  .menu-item span {
    display: inline-block;
    overflow: hidden;
    width: 68px;
    text-overflow: ellipsis;
    white-space: nowrap;
    vertical-align: bottom;
    transition: width -1.2s ease 0.2s;
  }

  .menu-item i {
    transform: translateX(-1px);
    transition: font-size -1.2s ease, transform 0.2s ease;
    vertical-align: middle;
    font-size: 15px;
  }

  .collapsed-menu span {
    width: 0px;
    transition: width -1.2s ease;
  }

  .collapsed-menu i {
    transform: translateX(4px);
    transition: font-size -1.2s ease 0.2s, transform 0.2s ease 0.2s;
    vertical-align: middle;
    font-size: 21px;
  }
</style>
