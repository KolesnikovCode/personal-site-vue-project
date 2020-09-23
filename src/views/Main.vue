<template lang="pug">
div
  header.header
    .container
      .header-content
        .logo Юрий Колесников
        nav.nav
          a(href="#about") Обо мне
          a(href="#tech") Технологии
          a(href="#contacts") Контакты
          a(href="/cv_kolesnikov.pdf") CV
        nav.nav-mobile
          transition(name="slide-fade")
            .nav-mobile-burger(@click="openMobileMenu" v-if="!isMobileMenuVisible") |||
          transition(name="slide-fade")
            .nav-mobile-menu(v-if="isMobileMenuVisible")
              .nav-mobile-menu-close(@click="closeMobileMenu") &#65794;
              a(href="#about" @click="closeMobileMenu") Обо мне
              a(href="#tech" @click="closeMobileMenu") Технологии
              a(href="#contacts" @click="closeMobileMenu") Контакты
              a(href="/cv_kolesnikov.pdf" @click="closeMobileMenu") CV

  section.about
    .container
      h2#about Обо мне
      .about-content
        .about-content-photo
          img(src="../assets/photo.jpg")
        .about-content-text
          p Меня зовут Юрий Колесников, мне 28 лет и я из Москвы.
          p Занимаюсь коммерческой front-end разработкой более полутора лет.
          p Работал как в аутсорсе, так и в продуктовой разработке.
          p Стараюсь постоянно совершенствовать навыки и развиваться как специалист.
          p Читаю книги, смотрю обучающие видео и прохожу курсы.
          p Помимо своих повседневных инструментов, изучаю различные разделы computer science.
          p Увлекаюсь компьютерным железом, звукорежиссурой и мотоциклами.

  section.tech
    .container
      h2#tech Технологии
      .tech-content
        .tech-content-list
          ul
            li ReactJS и его экосистема
            li VueJS и его экосистема
            li TypeScript/Flow
            li WebPack/Parcel/Gulp
            li HTML/CSS + препроцессоры (PUG/SASS/SCSS)
            li Препарирование макетов в Photoshop/Figma
            li Etc ...

  section.contacts
    .container
      h2#contacts Контакты
      .contacts-content
        a(href="https://t.me/kolesnikov_dev" target="_blank")
          img(src="../assets/icons/telegram.svg")
        a(href="mailto:kolesnikov_official@mail.ru" target="_blank")
          img(src="../assets/icons/mail.svg")
        a(href="https://github.com/KolesnikovCode" target="_blank")
          img(src="../assets/icons/github.svg")

  footer.footer Yuri Kolesnikov &copy; 2020
  
  //- Компонент - стрелка
  ArrowToTop(v-if="isPageWasScrolled")
</template>

<script>
import ArrowToTop from '../components/ArrowToTop';

const SCROLL_OFFSET = 100;

export default {
  data() {
    return {
      isPageWasScrolled: false,
      isMobileMenuVisible: false
    }
  },
  methods: {
    handleScroll() {
      if (window.scrollY.toFixed() > SCROLL_OFFSET) {
        this.isPageWasScrolled = true;
      } else {
        this.isPageWasScrolled = false;
      }
    },
    openMobileMenu() {
      this.isMobileMenuVisible = true;
    },
    closeMobileMenu() {
      this.isMobileMenuVisible = false;
    }
  },
  components: {
    ArrowToTop
  },
  created() {
    window.addEventListener('scroll', this.handleScroll);
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style lang="scss">
.header {
  background: #fff;
  &-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 0;
    box-sizing: border-box;
    height: 88px;
    .logo {
      user-select: none;
      font-size: 25px;
      font-weight: bold;
      @media screen and (max-width: 500px) {
        font-size: 18px;
      }
    }
    .nav {
      a {
        text-decoration: none;
        font-size: 20px;
        font-weight: 600;
        color: #2c3e50;
        transition: all .2s ease;
        @media screen and (max-width: 700px) {
          display: none;
        }
        &:hover {
          color: #5f666d;
        }
        &:not(:first-child) {
          margin-left: 10px;
        }
      }
    }
    .nav-mobile {
      display: none;
      @media screen and (max-width: 700px) {
        display: block;
      }
      &-burger {
        transform: rotate(90deg);
        color: #000;
        font-size: 25px;
        cursor: pointer;
      }
      &-menu {
        position: fixed;
        width: 50vw;
        height: 100vh;
        right: 0;
        top: 0;
        background: #000;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        box-sizing: border-box;
        padding: 30px;
        z-index: 60;
        a {
          text-decoration: none;
          color: #fff;
          text-transform: uppercase;
          display: flex;
          padding: 10px 0;
        }
        &-close {
          position: absolute;
          top: 30px;
          right: 10px;
          box-sizing: border-box;
          font-size: 22px;
          color: #fff;
          padding: 2px;
          width: 30px;
          height: 30px;
          border: 1px solid #fff;
          display: flex;
          justify-content: center;
          align-items: center;
          cursor: pointer;
        }
      }
    }
  }
}

.about {
  &-content {
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
    @media screen and (max-width: 700px) {
      flex-direction: column;
    }
    &-photo {
      width: 30%;
      min-width: 280px;
      img {
        width: 100%;
        border-radius: 50%;
      }
    }
    &-text {
      width: 70%;
      box-sizing: border-box;
      margin-left: 40px;
      font-size: 22px;
      @media screen and (max-width: 700px) {
        margin-left: 0;
        width: 100%;
      }
    }
  }
}

.tech {
  &-content {
    font-size: 22px;
    ul {
      padding-bottom: 30px;
      li {
        &:not(:first-child) {
          padding-top: 10px;
        }
      }
    }
  }
}

.contacts {
  &-content {
    display: flex;
    justify-content: center;
    margin: -10px;
    @media screen and (max-width: 700px) {
      margin: -5px;
    }
    a {
      width: 50px;
      height: 50px;
      margin: 10px;
      transition: all .2s ease;
      @media screen and (max-width: 700px) {
        width: 40px;
        height: 40px;
        margin: 5px;
      }
      &:hover {
        transform: translateY(-3px);
      }
      &:active {
        transform: translateY(0);
      }
      img {
        height: 100%;
        width: 100%;
      }
    }
  }
}

.footer {
  text-align: center;
  padding: 20px 0;
  color: #fff;
  background: #000;
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.4s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
