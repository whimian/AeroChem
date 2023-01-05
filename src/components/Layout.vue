<template>
  <a-layout style="min-height: 100vh">
    <a-layout-sider v-model:collapsed="collapsed" collapsible>
      <div class="logo">
        <img
          src="/src/assets/AVIC_LOGO - White-transparent.svg"
          style="width: 32px; margin: 16px"
        />
        <span style="color: white; font-size: 24px">CAPDI</span>
      </div>

      <a-menu v-model:selectedKeys="selectedKeys" theme="dark" mode="inline">
        <a-sub-menu :key="menu.key" v-for="menu in menuList">
          <template #title>
            <span>
              <user-outlined />
              <span>{{ menu.name }}</span>
            </span>
          </template>
          <a-menu-item :key="sub.key" v-for="sub in menu.subs">
            {{ sub.name }}
          </a-menu-item>
        </a-sub-menu>
      </a-menu>
    </a-layout-sider>

    <a-layout>
      <a-layout-header style="background: #fff; padding: 0" />
      <a-layout-content style="margin: 0 16px">
        <a-breadcrumb style="margin: 16px 0">
          <a-breadcrumb-item>User</a-breadcrumb-item>
          <a-breadcrumb-item>Bill</a-breadcrumb-item>
        </a-breadcrumb>
        <div
          :style="{ padding: '24px', background: '#fff', minHeight: '360px' }"
        >
          Bill is a cat.
        </div>
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        CAPDI ©2023
      </a-layout-footer>
    </a-layout>
  </a-layout>
</template>

<script>
import {
  PieChartOutlined,
  DesktopOutlined,
  UserOutlined,
  TeamOutlined,
  FileOutlined,
} from '@ant-design/icons-vue';
import { defineComponent, ref } from 'vue';

let id = 1;
export default defineComponent({
  components: {
    PieChartOutlined,
    DesktopOutlined,
    UserOutlined,
    TeamOutlined,
    FileOutlined,
  },
  data() {
    return {
      collapsed: ref(false),
      selectedKeys: ref(['1']),
      menuList: [
        {
          name: '槽液管理',
          key: id++,
          subs: [
            { name: '分析周期管理', key: id++ },
            { name: '分析任务管理', key: id++ },
          ],
        },
        {
          name: '质量管理',
          key: id++,
          subs: [
            { name: '批次质检管理', key: id++ },
            { name: '定期试验管理', key: id++ },
          ],
        },
      ],
    };
  },
});
</script>

<style>
/* #components-layout-demo-side .logo {
  height: 64px;
  margin: 16px;
  background: rgba(255, 255, 255, 0.3);
} */

.site-layout .site-layout-background {
  background: #fff;
}
[data-theme='dark'] .site-layout .site-layout-background {
  background: #141414;
}

.ant-layout {
  display: flex;
  width: 100%;
  min-height: 100%;
}

.ant-menu {
  padding: 0px;
}

.logo {
  height: 64px;
  /* padding: 16px; */
}
</style>
