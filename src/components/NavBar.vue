<template>
  <nav class="navbar custom-navbar">
    <div class="container-fluid px-4 d-flex justify-content-between align-items-center">
      <!-- 左侧 Logo + 品牌 -->
      <a class="navbar-brand d-flex align-items-center gap-2" href="#">
        <span class="fs-4">🚘</span>
        <span class="fw-bold brand-text">Melbourne Parking</span>
      </a>

      <!-- 中部导航 -->
      <ul class="nav align-items-center gap-3">
        <li class="nav-item">
          <a class="nav-link" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">About Us</a>
        </li>
        <li class="nav-item custom-dropdown"
            @mouseenter="showMenu"
            @mouseleave="scheduleHideMenu">
          <a class="nav-link" href="#">Features</a>
          <ul class="dropdown-menu" 
              :class="{ show: dropdownVisible }"
              @mouseenter="cancelHideMenu" 
              @mouseleave="scheduleHideMenu">
            <li class="dropend" 
                @mouseenter="showSubMenu" 
                @mouseleave="scheduleHideSubMenu">
              <a href="#" class="dropdown-item sub-dropdown-toggle">Data Insights ▸</a>
              <ul class="dropdown-menu sub-menu" 
                  :class="{ show: subDropdownVisible }"
                  @mouseenter="cancelHideSubMenu" 
                  @mouseleave="scheduleHideSubMenu">
                <li><a class="dropdown-item" href="#">Car Owner Trend Report</a></li>
                <li><a class="dropdown-item" href="#">Population Growth Report</a></li>
              </ul>
            </li>
            <li><a class="dropdown-item" href="#">Live Parking Map</a></li>
            <li><a class="dropdown-item" href="#">Predictive Forecast</a></li>
            <li><a class="dropdown-item" href="#">Forecast 2</a></li>
          </ul>
        </li>
      </ul>

      <!-- 右侧登录注册 -->
      <div class="d-flex align-items-center gap-2">
        <a class="btn btn-outline-primary" href="#">Login</a>
        <a class="btn btn-primary" href="#">Register</a>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const dropdownVisible = ref(false)
const subDropdownVisible = ref(false)
let hideTimeout = null
let subMenuTimeout = null

function showMenu() {
  clearTimeout(hideTimeout)
  dropdownVisible.value = true
}

function scheduleHideMenu() {
  hideTimeout = setTimeout(() => {
    dropdownVisible.value = false
    subDropdownVisible.value = false
  }, 300)
}

function cancelHideMenu() {
  clearTimeout(hideTimeout)
}

function showSubMenu() {
  clearTimeout(subMenuTimeout)
  subDropdownVisible.value = true
}

function scheduleHideSubMenu() {
  subMenuTimeout = setTimeout(() => {
    subDropdownVisible.value = false
  }, 300)
}

function cancelHideSubMenu() {
  clearTimeout(subMenuTimeout)
}
</script>

<style scoped>
.custom-navbar {
  background: linear-gradient(to right, #f8f9fa, #e6ecf1);
  padding: 8px 0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  z-index: 10;
}

.navbar-brand {
  font-size: 1.25rem;
  padding: 0;
  margin: 0;
}

.brand-text {
  font-size: 1.1rem;
  font-weight: 600;
  color: #000;
}

.nav-link {
  padding: 0.5rem 0;
  font-weight: 500;
  color: #333;
  transition: color 0.2s ease;
}

.nav-link:hover {
  color: #0d6efd;
}

.custom-dropdown {
  position: relative;
}

.dropdown-menu {
  position: absolute;
  top: calc(100% + 10px);
  left: 0;
  display: block;
  min-width: 220px;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
  padding: 0.5rem 0;
  z-index: 999;
  opacity: 0;
  visibility: hidden;
  transform: translateY(10px);
  transition: all 0.3s ease;
  pointer-events: none;
}

.dropdown-menu.show {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
  pointer-events: auto;
}

.dropdown-menu li a {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  font-size: 15px;
  font-weight: 500;
  color: #333;
  text-decoration: none;
  transition: background 0.2s ease, color 0.2s ease;
  border-radius: 6px;
}

.dropdown-menu li a:hover {
  background-color: #f6f6f6;
  color: #0d6efd;
}

.dropend {
  position: relative;
}

.sub-menu {
  position: absolute;
  top: 0;
  left: 100%;
  margin-left: 4px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(10px);
  transition: all 0.3s ease;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  min-width: 220px;
  padding: 0.5rem 0;
  z-index: 1000;
  pointer-events: none;
}

.sub-menu.show {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
  pointer-events: auto;
}

.btn {
  padding: 0.4rem 1rem;
  font-weight: 600;
  border-radius: 6px;
  transition: background 0.3s ease;
}

.btn-outline-primary {
  border: 2px solid #0d6efd;
  color: #0d6efd;
  background-color: transparent;
}

.btn-outline-primary:hover {
  background-color: #0d6efd;
  color: white;
}

.btn-primary {
  background-color: #0d6efd;
  color: white;
  border: none;
}

.btn-primary:hover {
  background-color: #0b5ed7;
}
</style>