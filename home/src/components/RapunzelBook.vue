<template>
  <div class="container">
    <div class="book" :class="{ 'open-book': isOpen }">
      <div class="page left" v-if="isOpen">
        <h1>Welcome to the Adventure!</h1>
        <p>Enjoy the magical journey of Rapunzel.</p>
      </div>
      <div class="page right" :class="{ open: isOpen }">
        <div class="front">
          <h1>Hello There!</h1>
          <p>Are you ready to get started?</p>
          <button class="continue-btn" @click="flipPage">Click to Continue</button>
        </div>
        <div class="back">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    flipPage() {
      this.isOpen = true;
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Parisienne&display=swap');

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('https://i.pinimg.com/originals/5d/e5/49/5de5498c524cf1cc3f48c6d1adced94a.jpg') no-repeat center center/cover;
  transition: justify-content 1s;
}

.book {
  width: 450px;
  height: 550px;
  position: relative;
  perspective: 1200px;
  transition: transform 1s;
}

.book.open-book {
  display: flex;
  width: 900px;
  justify-content: center;
}

.page {
  width: 450px;
  height: 100%;
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #a68bc5;
  border-radius: 10px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
  text-align: center;
  font-family: 'Parisienne', cursive;
  font-size: 30px;
  padding: 20px;
  transition: transform 1s;
  backface-visibility: hidden;
  color: #fff;
}

/* Left page (appears when opened) */
.left {
  background: #6a5acd;
  position: relative;
}

/* Right page with flipping effect */
.right {
  transform-origin: left;
  background: #b39ddb;
  transform-style: preserve-3d;
}

.right .front, .right .back {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  backface-visibility: hidden;
}

.right .back {
  transform: rotateY(180deg);
  background: #d1c4e9;
}

.right.open {
  transform: rotateY(-180deg);
}

.continue-btn {
  margin-top: 20px;
  padding: 12px 24px;
  background: #7e57c2;
  border: none;
  color: white;
  font-size: 22px;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s;
}

.continue-btn:hover {
  background: #5e35b1;
}
</style>
