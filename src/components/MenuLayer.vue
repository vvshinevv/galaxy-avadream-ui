<template>
  <div class="menu-layer mobile-only">
    <button type="button" class="icon-menu" @click="showModal = true">
        <svg xmlns="http://www.w3.org/2000/svg" width="80" height="80" viewBox="0 0 80 80">
            <path data-name="사각형 121" style="fill:none" d="M0 0h80v80H0z"/>
            <g data-name="그룹 308">
                <path data-name="선 4" transform="translate(15 25)" style="stroke:#fff;fill:none" d="M0 0h50"/>
                <path data-name="선 5" transform="translate(15 40)" style="stroke:#707070;fill:none" d="M0 0h50"/>
                <path data-name="선 6" transform="translate(15 40)" style="stroke:#fff;fill:none" d="M0 0h50"/>
                <path data-name="선 7" transform="translate(15 55)" style="stroke:#fff;fill:none" d="M0 0h50"/>
            </g>
        </svg>

    </button>
    <!--[D] on 클래스 추가시 확성화 -->
    <div class="menu-layer-box" :class="{ on: showModal === true }">
      <ul class="menu-layer-list">
        <li class="menu-layer-item">
          <a href="#" target="_blank"  class="menu-layer-link" @click.native="showModal = false">
            아바드림 세계관 보러가기
          </a>
        </li>
        <li class="menu-layer-item">
          <a href="#" target="_blank"  class="menu-layer-link" @click.native="showModal = false">
            티비조선 바로가기
          </a>
        </li>
      </ul>
      <button type="button" class="icon-close" @click="showModal = false" >
        <svg xmlns="http://www.w3.org/2000/svg" width="66" height="66" viewBox="0 0 66 66">
          <g data-name="그룹 1817">
            <path data-name="선 16" transform="translate(17.5 17.5)" style="fill:none;stroke:#fff;stroke-width:2px" d="M30 0 0 30"/>
            <path data-name="선 17" transform="rotate(90 15 32.5)" style="fill:none;stroke:#fff;stroke-width:2px" d="M30 0 0 30"/>
            <path data-name="사각형 872" style="fill:none" d="M0 0h66v66H0z"/>
          </g>
        </svg>

      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenuLayer",
  data() {
    return {
      showModal: false,
    };
  },
};
</script>

<style scoped>
.icon-close{
  width: 40px;
  height:40px;
}
.icon-close svg{
  width: 100%;
  height: 100%;
}
</style>
