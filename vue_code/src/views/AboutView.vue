<script>

</script>

<template>
  <div class="about">
    <div><span>Sass 星空</span></div>
    <div class="itme1"></div>
    <div class="itme2"></div>
    <div class="itme3"></div>
    <div class="itme4"></div>
    <div class="itme5"></div>
  </div>
</template>

<style lang="scss" scoped>
  .about {
    width: 100vw;
    height: 100vh;
    background:  linear-gradient(#10192c, #2d3a56);
    font-weight: 300;
    text-align: center;
    line-height: 100vh;
    font-size: 25px;
    color: #fff;

    @function getShadows($n) {
      $shadows: '#{random(100)}vw #{random(100)}vh #fce172';
      @for $i from 2 through $n {
        $shadows: '#{$shadows}, #{random(100)}vw #{random(100)}vh #fce172'
      }
      @return unquote($shadows);
    }

    @keyframes moveup {
      to {
        transform: translateY(-100vh);
      }
    }

    $durationto: 1000s;
    $count: 1000;
    @for $i from 1 through 5 {
      $durationto: floor($durationto / 2);
      $count: floor($count / 2);
        .itme#{$i} {
        $size: #{$i}px;
        $duration: $durationto;
        width: $size;
        height: $size;
        position: fixed;
        top: 0;
        left: 0;
        background-color: #fff;
        border-radius: 50%;
        box-shadow: getShadows($count);
        animation: moveup $duration linear infinite;
        &::after {
          content: "";
          position: fixed;
          width: inherit;
          height: inherit;
          left: 0;
          top: 100vh;
          border-radius: inherit;
          box-shadow: inherit;
        }
      }
    }
  }
</style>
