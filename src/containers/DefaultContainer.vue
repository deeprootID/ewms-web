<template>
  <div class="app" :class="[ asideOpen ? 'aside-menu-lg-show' : '' ]">
    <AppHeader fixed>
      <SidebarToggler class="d-lg-none" display="md" mobile />
      <b-link class="navbar-brand" to="#">
        <img class="navbar-brand-full" src="img/brand/logo-ewms.svg" width="89" height="25" alt="Logo">
        <img class="navbar-brand-minimized" src="img/brand/logo-ewms-min.svg" width="30" height="30" alt="Logo">
      </b-link>
      <SidebarToggler class="d-md-down-none" display="lg" :defaultOpen=true :hidden=true />
      <!-- <b-navbar-nav class="d-md-down-none">
        <b-nav-item class="px-3" to="/dashboard">Dashboard</b-nav-item>
        <b-nav-item class="px-3" to="/users" exact>Users</b-nav-item>
        <b-nav-item class="px-3">Settings</b-nav-item>
      </b-navbar-nav> -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item class="d-md-down-none">
          <!-- <i class="icon-bell"></i>
          <b-badge pill variant="danger">5</b-badge> -->
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <!-- <i class="icon-list"></i> -->
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <!-- <i class="icon-location-pin"></i> -->
        </b-nav-item>
        <DefaultHeaderDropdownAccnt/>
      </b-navbar-nav>
      <!-- <AsideToggler class="d-none d-lg-block" ref="aside" :defaultOpen="asideOpen ? true : false" /> -->
      <!--<AsideToggler class="d-lg-none" mobile />-->
    </AppHeader>
    <div class="app-body">
      <AppSidebar fixed>
        <SidebarHeader/>
        <SidebarForm/>
        <SidebarNav v-if="userRole === 'Pemasaran'" :navItems="navM"></SidebarNav>
        <SidebarNav v-else-if="userRole === 'Peralatan'" :navItems="navP"></SidebarNav>
        <SidebarNav v-else-if="userRole === 'Gudang'" :navItems="nav"></SidebarNav>
        <SidebarFooter/>
        <SidebarMinimizer/>
      </AppSidebar>
      <main class="main">
        <!-- <Breadcrumb :list="list"/> -->
        <div class="container-fluid">
          <router-view></router-view>
        </div>
      </main>
      <AppAside fixed>
        <!--aside-->
        <DefaultAside/>
      </AppAside>
    </div>
    <!-- <TheFooter> -->
      <!--footer-->
      <!-- <div>
        <a href="https://coreui.io">CoreUI</a>
        <span class="ml-1">&copy; 2018 creativeLabs.</span>
      </div>
      <div class="ml-auto">
        <span class="mr-1">Powered by</span>
        <a href="https://coreui.io">CoreUI for Vue</a>
      </div>
    </TheFooter> -->
  </div>
</template>

<script>
import nav from '@/_nav'
import navM from '@/_navM'
import navP from '@/_navP'
import { Header as AppHeader, SidebarToggler, Sidebar as AppSidebar, SidebarFooter, SidebarForm, SidebarHeader, SidebarMinimizer, SidebarNav, Aside as AppAside, AsideToggler, Footer as TheFooter, Breadcrumb } from '@coreui/vue'
import DefaultAside from './DefaultAside'
import DefaultHeaderDropdownAccnt from './DefaultHeaderDropdownAccnt'

export default {
  name: 'DefaultContainer',
  components: {
    AsideToggler,
    AppHeader,
    AppSidebar,
    AppAside,
    TheFooter,
    Breadcrumb,
    DefaultAside,
    DefaultHeaderDropdownAccnt,
    SidebarForm,
    SidebarFooter,
    SidebarToggler,
    SidebarHeader,
    SidebarNav,
    SidebarMinimizer
  },
  data () {
    return {
      nav: nav.items,
      navM: navM.items,
      navP: navP.items
    }
  },
  props: {
    asideOpen: Boolean,
    userRole: String
  },
  computed: {
    name () {
      return this.$route.name
    },
    list () {
      return this.$route.matched.filter((route) => route.name || route.meta.label )
    },
  },
  mounted () {
    this.userRole="Gudang";
    if (this.$route.path === "/dashboard") {
      this.asideOpen=true;
    }
  },
  watch: {
    $route: function() {
      this.userRole="Gudang";
      if (this.$route.path === "/dashboard") {
        this.asideOpen=true;
      } else  {
        this.asideOpen=false;
      }
    }
  }
}
</script>
