<template>
  <div class="navbar">
    <div class="navbar__left">
      <img src="../assets/logo.svg" class="navbar__left__logo" alt="logo" />
      <nav class="navbar__left__links">
        <a
          class="link"
          v-for="(item, idx) in links"
          v-bind:key="idx"
          href="#"
          >{{ item }}</a
        >
      </nav>
      <div class="navbar__left__search">
        <img src="../assets/cart.png" alt="cart" />Поиск услуг
      </div>
    </div>
    <div class="navbar__right">
      <menu class="navbar__right__menu">
        <img
          :src="item"
          :alt="item"
          v-for="(item, idx) in pics"
          v-bind:key="idx"
        />
      </menu>
      <div class="dropdown" tabindex="1">
        <i class="db2" tabindex="1"></i
        ><a class="dropbtn r i2">{{ usrInit }}</a>
        <div class="dropdown-content r">
          <p>{{ userName }}</p>
          <p class="drop__balance">Тривио баланс - 598 Р</p>
          <p class="drop__debts">Задолженность - 0 Р</p>
          <p>Профиль</p>
          <p>Управление</p>
          <p>Компания</p>
          <p class="drop__exit">Выход</p>
        </div>
      </div>
      <img class="navbar__right__lang" src="../assets/rus.png" alt="rus" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: ["Рабочий стол", "Проекты", "Отчеты", "Мои закладки", "Финансы"],
      pics: [
        require("../assets/search.png"),
        require("../assets/alert.png"),
        require("../assets/timer.png"),
        require("../assets/hearth.png"),
        require("../assets/email.png"),
      ],
      usrInit: "AD",
      userName: "Alexey Demichev",
    };
  },
  name: "NavbarItem",
};
</script>

<style scoped lang="scss">
$font-stack: 14px Helvetica, sans-serif;
$primary-color: #000047;
$link-color: black;

%flex {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

%links {
  font: $font-stack;
  text-decoration: none;
  color: $link-color;
  display: inline-block;
  position: relative;
  &:after {
    content: "";
    position: absolute;
    width: 100%;
    transform: scaleX(0);
    height: 1px;
    bottom: 0;
    left: 0;
    background-color: black;
    transform-origin: bottom right;
    transition: transform 0.25s ease-out;
  }

  &:hover:after {
    transform: scaleX(1);
    transform-origin: bottom left;
  }
}

.navbar {
  width: 100vw;
  height: 75px;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  @extend %flex;
  &__left {
    @extend %flex;
    margin-left: 20px;
    &__logo {
      max-width: 100px;
      margin-right: 40px;
      cursor: pointer;
    }
    &__links {
      a {
        @extend %links;
        margin-right: 20px;
      }
    }
    &__search {
      padding: 10px;
      border-radius: 10px;
      background: rgba($color: $primary-color, $alpha: 0.2);
      transition: 0.25s;
      img {
        max-width: 10px;
        margin-right: 5px;
      }
      &:hover {
        background: white;
        cursor: pointer;
      }
    }
  }
  &__right {
    @extend %flex;
    &__menu {
      img {
        max-width: 20px;
        margin-right: 20px;
        cursor: pointer;
        transition: 0.35s ease-out;
        &:hover {
          transform: scale(1.3);
          transition: 0.35s ease-out;
        }
      }
    }
    &__lang {
      max-width: 25px;
      height: 20px;
      border-radius: 50%;
      margin: 0 20px 0 20px;
      border: 1px solid lightgray;
      cursor: pointer;
      transition: 0.35s ease-out;
      &:hover {
        transform: scale(1.3);
        transition: 0.35s ease-out;
      }
    }
    &__user {
      display: inline-block;
      position: relative;
      color: $primary-color;
      padding: 10px;
      border-radius: 10px;
      background: rgba($color: $primary-color, $alpha: 0.2);
      transition: 0.25s;
      &:hover {
        background: white;
        cursor: pointer;
      }
    }
  }
}

.dropdown {
  color: $primary-color;
  padding: 10px;
  border-radius: 10px;
  display: inline-block;
  position: relative;
  .dropdown-content {
    position: absolute;
    top: 90%;
    visibility: hidden;
    opacity: 0;
    z-index: 100000;
    background-color: #f7f7f7;
    min-width: 200%;
    padding: 10px;
    font-size: 16px;
    box-shadow: 0px 8px 16px rgba(0, 0, 0, 0.2);
    transition: 0.35s ease-out;
    p {
      margin-bottom: 5px;
    }
  }
  .dropdown-content.r {
    right: 0;
    .drop__balance {
      color: lightgray;
    }
    .drop__debts {
      color: lightgray;
    }
    .drop__exit {
      margin-top: 15px;
    }
  }
  &:focus {
    .dropbtn {
      background: rgba($color: $primary-color, $alpha: 0.2);
      &::after {
        height: 0;
        border-bottom: 0;
        margin-bottom: 4px;
      }
    }
    .dropdown-content {
      outline: none;
      visibility: visible;
      opacity: 1;
      transform: translateY(20px);
    }
    .db2 {
      display: inline-block;
    }
  }
  .db2 {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    opacity: 0;
    cursor: pointer;
    z-index: 10;
    display: none;
  }
}

.dropbtn {
  display: inline-block;
  padding: 12px 16px;
  color: $primary-color;
  cursor: pointer;
  transition: 0.35s ease-out;
  &:hover {
    background: rgba($color: $primary-color, $alpha: 0.2);
  }
  &::after {
    content: "";
    display: inline-block;
    width: 15px;
    height: 3px;
    margin-left: 10px;
    border-top: 2px solid #fff;
    border-bottom: 7px double #fff;
  }
}

.dropdown .db2:focus .dropdown-content,
.dropdown-content .db3:focus .dropdown-content {
  outline: none;
  visibility: hidden;
  opacity: 0;
}

.dropbtn.i2::after {
  content: "";
  display: inline-block;
  border: 0;
  width: 15px;
  height: 12px;
  margin-left: 10px;
  background: linear-gradient(to right, #fff, #fff) 0px 0px/11px 2px,
    linear-gradient(to right, #fff, #fff) 0px 5px/15px 2px,
    linear-gradient(to right, #fff, #fff) 0px 10px/8px 2px;
  background-repeat: no-repeat;
}
.dropdown:focus .dropbtn.i2::after {
  width: 15px;
  height: 10px;
  background: linear-gradient(to right, #fff, #fff) 0px 10px/15px 2px;
  background-repeat: no-repeat;
}
</style>
