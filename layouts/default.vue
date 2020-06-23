<template>
  <div>
    <header class="main_h">
      <div class="row">
        <a class="logo" href="#">M.2DEV</a>

        <div class="mobile-toggle">
          <span></span>
          <span></span>
          <span></span>
        </div>

        <nav>
          <ul>
            <li><a href=".profile">Profile</a></li>
            <li><a href=".gallery">Gallery</a></li>
            <li><a href=".portfolio">Portfolio</a></li>
            <li><a href=".contact">Contact</a></li>
          </ul>
        </nav>
      </div>
      <!-- / row -->
    </header>
    <Nuxt />
  </div>
</template>
<script>
import $ from "jquery";
export default {
  mounted() {
    // Sticky Header
    $(window).scroll(function() {
      if ($(window).scrollTop() > 100) {
        $(".main_h").addClass("sticky");
      } else {
        $(".main_h").removeClass("sticky");
      }
    });

    // Mobile Navigation
    $(".mobile-toggle").click(function() {
      if ($(".main_h").hasClass("open-nav")) {
        $(".main_h").removeClass("open-nav");
      } else {
        $(".main_h").addClass("open-nav");
      }
    });

    $(".main_h li a").click(function() {
      if ($(".main_h").hasClass("open-nav")) {
        $(".navigation").removeClass("open-nav");
        $(".main_h").removeClass("open-nav");
      }
    });

    // navigation scroll lijepo radi materem
    $("nav a").click(function(event) {
      const id = $(this).attr("href");
      const offset = 70;
      const target = $(id).offset().top - offset;
      $("html, body").animate(
        {
          scrollTop: target
        },
        500
      );
      event.preventDefault();
    });
  }
};
</script>
<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
</style>
