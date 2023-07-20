<script setup></script>

<template>
  <div class="row">
    <div class="page-section sidebar">
      <div class="sidebar-inner-section">
        <div class="list-section"></div>
        <div class="button">Submit button</div>
      </div>
    </div>
    <div class="page-section main-area grid-section" style="background-color: yellow">
      <div class="box" style="background-color: orange">One</div>
      <div class="box" style="background-color: pink">Two</div>
      <div class="box" style="background-color: violet">Three</div>
      <div class="box" style="background-color: brown">Four</div>
    </div>
  </div>
  <img alt="Vue logo" class="trash-icon" src="@/assets/trash-icon.png" width="125" height="125" />
  <div class="icon-bar">
    <a class="active" href="#"><i class="fa fa-home"></i></a>
    <a href="#"><i class="fa fa-search"></i></a>
    <a href="#"><i class="fa fa-envelope"></i></a>
    <a href="#"><i class="fa fa-globe"></i></a>
    <a href="#"><i class="fa fa-trash"></i></a>
  </div>
</template>

<style scoped lang="scss">
.sidebar {
  float: left;
  width: 33.33%;
  height: 100vh;
  background-color: white;
  display: flex;
  align-items: stretch;

  .sidebar-inner-section {
    width: 100%;
    display: flex;
    flex-direction: column;
    margin: 20px;
    background-color: violet;

    .list-section {
      height: 90%;
      background-color: blue;
      margin: 20px;
    }

    .button {
      padding: 15px;
      font-size: 17px;
      color: #fff;
      border-radius: 30px;
      background: #428cb5;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      margin: auto 10px 10px 10px;
    }
  }
}

.main-area {
  float: left;
  width: 66.67%;
  height: 100vh;
}

.grid-section {
  display: flex;
  flex-flow: row wrap;

  .box {
    flex-basis: 50%;
  }
}

/* Clear floats after the columns */
.row:after {
  content: '';
  display: table;
  clear: both;
}

.trash-icon {
  position: fixed;
  bottom: 10px;
  right: 10px;
}

.icon-bar {
  width: 90px;
  background-color: #555;
  position: absolute;
  top: 10px;
  right: 10px;

  a {
    display: block;
    text-align: center;
    padding: 16px;
    transition: all 0.3s ease;
    color: white;
    font-size: 36px;
  }

  a:hover {
    background-color: #000;
  }

  .active {
    background-color: #04aa6d;
  }
}

/* Responsive layout - when the screen is less than 600px wide */
@media screen and (max-width: 600px) {
  .page-section {
    width: 100%;
  }

  .grid-section {
    .box {
      flex-basis: 100%;
    }
  }
}
</style>
