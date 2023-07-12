<template>
  <div class="container_hero">
    <div class="container_search">
      <div class="container_heading">
        <h1 class="heading">Trova subito il tuo insegnante.</h1>
      </div>
      <div class="container_teach">
        <div class="ct_rounded_corner" :class="{ activated_field: isFieldSearchActive }">
          <div class="ct_field">
            <div class="d_flexed box_icon">
              <i class="fa-solid fa-magnifying-glass"></i>
            </div>
            <input type="text" class="field_search" v-model="searchBar" @input="fieldInput" @focus="activateFieldSearch" @blur="deactivateFieldSearch" placeholder="Cosa vuoi imparare?">
            <div class="dpd_menu_subjects" v-if="isFieldSearchActive">
              <ul class="list_subjects">
                <li class="heading_item">Scegli la materia da imparare</li>
                <li class="item_subject" v-for="(elem, index) in subject" :key="index">
                  <a href="/">{{ elem.nameSubject }}</a>
                </li>
              </ul>
            </div>
          </div>
          <div class="d_flexed ct_btn">
            <button type="button" class="btn">
              <i class="fa-solid fa-magnifying-glass"></i>
              <span class="label_btn">Cerca</span>
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="container_picture" ref="containerRef" @mousemove="handleMouseMove">
      <div class="margin">
        <div class="left_pic">
          <div class="box_image" :style="getParallaxStyle(leftPicOffsetX, leftPicOffsetY, 0)"
            style="position: relative; top: 47px; left: 54px; background-image: url(https://images.unsplash.com/photo-1534528741775-53994a69daeb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=928&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(leftPicOffsetX, leftPicOffsetY, 1)"
            style="position: relative; top: 51px; left: -102px; background-image: url(https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(leftPicOffsetX, leftPicOffsetY, 2)"
            style="position: relative; top: 78px; left: 34px; background-image: url(https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(leftPicOffsetX, leftPicOffsetY, 3)"
            style="position: relative; top: -19px; left: -141px; background-image: url(https://images.unsplash.com/photo-1517841905240-472988babdf9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
        </div>
        <div class="right_pic">
          <div class="box_image" :style="getParallaxStyle(rightPicOffsetX, rightPicOffsetY, 0)"
            style="position: relative; top: 46px; left: 27px; background-image: url(https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(rightPicOffsetX, rightPicOffsetY, 1)"
            style="position: relative; top: 19px; left: 258px; background-image: url(https://images.unsplash.com/photo-1524504388940-b1c1722653e1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(rightPicOffsetX, rightPicOffsetY, 2)"
            style="position: relative; top: 0; left: 73px; background-image: url(https://images.unsplash.com/photo-1501196354995-cbb51c65aaea?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1771&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(rightPicOffsetX, rightPicOffsetY, 3)"
            style="position: relative; top: -22px; left: 260px; background-image: url(https://images.unsplash.com/photo-1463453091185-61582044d556?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1770&q=80);">
          </div>
          <div class="box_image" :style="getParallaxStyle(rightPicOffsetX, rightPicOffsetY, 4)"
            style="position: relative; top: -75px; left: 45px; background-image: url(https://images.unsplash.com/photo-1488426862026-3ee34a7d66df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80);">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroComp",
  data() {
    return {
      mouseX: 0,
      mouseY: 0,
      leftPicOffsetX: 0,
      leftPicOffsetY: 0,
      rightPicOffsetX: 0,
      rightPicOffsetY: 0,
      isFieldSearchActive: false,
      subject: [
        { id: 1, nameSubject: 'Matematica' },
        { id: 2, nameSubject: 'Italiano' },
        { id: 3, nameSubject: 'Storia' },
        { id: 4, nameSubject: 'Geografia' },
        { id: 5, nameSubject: 'Scienze' },
        { id: 6, nameSubject: 'Inglese' },
        { id: 7, nameSubject: 'Arte' },
        { id: 8, nameSubject: 'Musica' },
        { id: 9, nameSubject: 'Educazione Fisica' },
        { id: 10, nameSubject: 'Tecnologia' },
        { id: 11, nameSubject: 'Religione' },
        { id: 12, nameSubject: 'Informatica' },
      ]
    };
  },
  mounted() {
    window.addEventListener('mousemove', this.updateMousePosition);
  },
  beforeDestroy() {
    window.removeEventListener('mousemove', this.updateMousePosition);
  },
  methods: {
    updateMousePosition(event) {
      this.mouseX = event.clientX;
      this.mouseY = event.clientY;
    },
    getParallaxStyle(offsetX, offsetY, index) {
      const sensitivity = 2; // Sensitivity of the parallax effect
      const translateX = `${offsetX * sensitivity * (index + 1)}px`;
      const translateY = `${offsetY * sensitivity * (index + 1)}px`;
      return `transform: translate(${translateX}, ${translateY});`;
    },
    handleMouseMove() {
      const containerRect = this.$refs.containerRef.getBoundingClientRect();
      const containerCenterX = containerRect.left + containerRect.width / 2;
      const containerCenterY = containerRect.top + containerRect.height / 2;

      this.leftPicOffsetX = (containerCenterX - this.mouseX) / containerRect.width;
      this.leftPicOffsetY = (containerCenterY - this.mouseY) / containerRect.height;

      this.rightPicOffsetX = (this.mouseX - containerCenterX) / containerRect.width;
      this.rightPicOffsetY = (this.mouseY - containerCenterY) / containerRect.height;
    },
    activateFieldSearch() {
      this.isFieldSearchActive = true;
    },
    deactivateFieldSearch() {
      this.isFieldSearchActive = false;
    }
  },
}
</script>

<style scoped>
.d_flexed {
  display: flex;
  align-items: center;
}

.container_hero {
  position: relative;
  z-index: 5;
  top: 0;
  left: 0;
  width: 100%;
  height: 85vh;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgb(137, 206, 148);
  background: linear-gradient(0deg, rgba(137, 206, 148, 0) 0%, rgba(137, 206, 148, 0.2) 100%);
}

.container_picture {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.margin {
  width: 90%;
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}

.left_pic,
.right_pic {
  /* position: relative; */
  top: 0;
  bottom: 0;
  width: 50%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.box_image {
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  width: 150px;
  height: 150px;
  aspect-ratio: 1;
  border-radius: 20px;
}

.heading {
  color: #000;
  font-size: 2.2rem;
  font-weight: 600;
  text-align: center;
}

.container_teach {
  margin-top: 40px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.ct_rounded_corner {
  height: 100%;
  display: flex;
  align-items: center;
  border-width: 2px;
  border-style: solid;
  border-color: #F1F1F1;
  padding: 6px;
  border-radius: 42px;
}

.ct_rounded_corner.activated_field{
  border-color: #89CE94;
}

.ct_field,
.ct_btn {
  position: relative;
  height: 100%;
  display: flex;
  align-items: center;
}

.box_icon {
  position: relative;
  height: 100%;
  padding: 0 20px;
  border-top-left-radius: 32px;
  border-bottom-left-radius: 32px;
  background: transparent;
  transition: all 150ms ease;
}

.box_icon i {
  color: #89CE94;
  font-size: 1rem;
}

.field_search {
  height: 100%;
  width: 300px;
  min-width: 200px;
  max-width: 300px;
  background: transparent;
  border: none;
  outline: none;
  padding-right: 20px;
  border-top-right-radius: 32px;
  border-bottom-right-radius: 32px;
  transition: all 150ms ease;
}

.ct_field:hover .field_search {
  background: #F1F1F1;
}

.ct_field:hover .box_icon {
  background: #F1F1F1;
}

.field_search::placeholder {
  color: #000;
  font-size: 1rem;
  font-weight: 400;
}

.btn {
  background: #89CE94;
  padding: 0 20px;
  height: 100%;
  border: none;
  outline: none;
  display: flex;
  align-items: center;
  border-radius: 32px;
  margin-left: 10px;
  cursor: pointer;
  transition: all 150ms ease;
}

.btn:hover {
  background: #7bb985;
}

.btn i {
  color: #000;
  font-size: 1rem;
}

.label_btn {
  color: #000;
  font-size: 1rem;
  font-weight: 400;
  margin-left: 10px;
}

.dpd_menu_subjects {
  position: absolute;
  top: 60px;
  left: 0;
  width: 100%;
  border-radius: 20px;
  text-align: left;
  padding: 20px 0;
  background: #fff;
  box-shadow: 0 0 1px rgba(0, 0, 0, .2);
  max-height: 300px;
  overflow-x: auto;
}

/* width */
.dpd_menu_subjects::-webkit-scrollbar {
  width: 3px;
}

/* Handle */
.dpd_menu_subjects::-webkit-scrollbar-thumb {
  background: #89CE94;
  border-radius: 10px;
}

.heading_item {
  color: #aaa;
  font-size: .8rem;
  font-weight: 600;
  padding: 0 20px;
  margin-bottom: 16px;
}

.item_subject {
  width: 100%;
  height: 45px;
  padding: 0 20px;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.item_subject:hover {
  background: #e7f5ea;
}

.item_subject a {
  color: #89CE94;
  font-size: 1rem;
  font-weight: 500;
}

/* Media Query's */
@media only screen and (max-width: 1290px) {
  .box_image {
    width: 100px;
    height: 100px;
    aspect-ratio: 1;
  }

  .margin {
    width: 100%;
    padding: 0 4%;
  }

  .container_search {
    width: 100%;
    padding: 0 4%;
  }

  .field_search {
    width: 100%;
  }
}
</style>