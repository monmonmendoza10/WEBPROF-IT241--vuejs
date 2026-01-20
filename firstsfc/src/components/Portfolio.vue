<template>
  <div class="portfolio-container">
    <header class="header">
      <h1>Vinz Szymone Roi V. Mendoza</h1>
    </header>

    <nav class="menu">
      <ul>
        <li><a href="#about" @click="scrollTo('about')">About Me</a></li>
        <li><a href="#contact" @click="scrollTo('contact')">Contact Info</a></li>
        <li><a href="#goals" @click="scrollTo('goals')">Goals</a></li>
        <li><a href="#gallery" @click="scrollTo('gallery')">Gallery</a></li>
      </ul>
    </nav>

    <main class="content">
      <section id="about">
        <h2>About Me</h2>
        <p>
          I'm Szymone, 19 years old, studying BSIT (Bachelor of Science in Information Technology).
          I'm passionate about technology and eager to expand my IT skills.
        </p>
        <p>{{ message }}</p>
      </section>

      <section id="contact">
        <h2>Contact Information</h2>
        <p>
          Email:
          <a href="mailto:mendozaszymone10@gmail.com">
            mendozaszymone10@gmail.com
          </a>
        </p>
      </section>

      <section id="goals">
        <h2>Goals</h2>
        <p>
          My goal is to become a successful IT professional and own multiple cars someday.
        </p>
      </section>
    </main>

    <section class="facts" id="gallery">
      <h2>Picture Gallery</h2>
      <div class="gallery-container">
        <div class="gallery-main">
          <img 
            :src="images[currentIndex].itemImageSrc" 
            :alt="images[currentIndex].alt"
            class="main-image"
          />
          <p class="image-title">{{ images[currentIndex].title }}</p>
          <p class="image-description">{{ images[currentIndex].alt }}</p>
        </div>

        <div class="gallery-controls">
          <button @click="previousImage" class="nav-button">← Previous</button>
          <span class="image-counter">{{ currentIndex + 1 }} / {{ images.length }}</span>
          <button @click="nextImage" class="nav-button">Next →</button>
        </div>

        <div class="gallery-thumbnails">
          <img 
            v-for="(image, index) in images" 
            :key="index"
            :src="image.thumbnailImageSrc" 
            :alt="image.alt"
            @click="currentIndex = index"
            class="thumbnail"
            :class="{ active: currentIndex === index }"
          />
        </div>
      </div>
    </section>

    <footer class="footer">
      <p>&copy; 2025 Vinz Szymone Roi V. Mendoza</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Portfolio',
  data() {
    return {
      message: "HELLO CRUSH🚀",
      currentIndex: 0,
      images: [
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria1.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria1s.jpg',
          alt: 'Beautiful landscape view',
          title: 'Image 1'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria2.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria2s.jpg',
          alt: 'Nature photography',
          title: 'Image 2'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria3.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria3s.jpg',
          alt: 'Scenic view',
          title: 'Image 3'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria4.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria4s.jpg',
          alt: 'Outdoor adventure',
          title: 'Image 4'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria5.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria5s.jpg',
          alt: 'Stunning photography',
          title: 'Image 5'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria6.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria6s.jpg',
          alt: 'Creative composition',
          title: 'Image 6'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria7.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria7s.jpg',
          alt: 'Artistic view',
          title: 'Image 7'
        },
        {
          itemImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria8.jpg',
          thumbnailImageSrc: 'https://primefaces.org/cdn/primevue/images/galleria/galleria8s.jpg',
          alt: 'Perfect moment',
          title: 'Image 8'
        },
        {
          itemImageSrc: 'https://static.vecteezy.com/system/resources/thumbnails/005/857/332/small/funny-portrait-of-cute-corgi-dog-outdoors-free-photo.jpg',
          thumbnailImageSrc: 'https://static.vecteezy.com/system/resources/thumbnails/005/857/332/small/funny-portrait-of-cute-corgi-dog-outdoors-free-photo.jpg',
          alt: 'Cute corgi dog',
          title: 'Corgi'
        }
      ]
    };
  },
  methods: {
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    },
    previousImage() {
      this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length;
    },
    scrollTo(id) {
      const element = document.getElementById(id);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    }
  },
  mounted() {
    console.log('Portfolio component loaded');
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.portfolio-container {
  display: grid;
  grid-template-areas:
    "header"
    "menu"
    "main"
    "facts"
    "footer";
  gap: 10px;
  background-color: white;
  font-family: "Lucida Sans", sans-serif;
  font-size: 17px;
  color: #333;
}

/* Header */
.header {
  grid-area: header;
  background-color: purple;
  text-align: center;
  color: #ffffff;
  padding: 20px;
}

.header h1 {
  font-size: 40px;
  margin: 0;
}

/* Menu */
.menu {
  grid-area: menu;
}

.menu ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.menu li {
  padding: 8px;
  margin-bottom: 7px;
  background-color: #33b5e5;
}

.menu li:hover {
  background-color: #0099cc;
}

.menu a {
  color: #ffffff;
  text-decoration: none;
  font-weight: bold;
  cursor: pointer;
}

/* Content */
.content {
  grid-area: main;
  padding: 10px;
}

.content section {
  margin-bottom: 20px;
}

.content h2 {
  color: #4CAF50;
  margin-top: 0;
}

.content p {
  margin-bottom: 7px;
}

.content a {
  color: #0099cc;
  text-decoration: none;
}

.content a:hover {
  text-decoration: underline;
}

/* Facts/Gallery */
.facts {
  grid-area: facts;
  border: 1px solid #0099cc;
  background-color: beige;
  padding: 10px;
}

.facts h2 {
  font-size: 20px;
}

.gallery-container {
  text-align: center;
}

.gallery-main {
  margin: 20px 0;
}

.main-image {
  width: 100%;
  max-width: 600px;
  height: auto;
  border-radius: 8px;
}

.image-title {
  font-size: 20px;
  font-weight: bold;
  margin: 10px 0;
}

.image-description {
  font-size: 16px;
  margin: 0 0 20px 0;
}

.gallery-controls {
  margin: 20px 0;
}

.nav-button {
  padding: 10px 20px;
  margin: 0 5px;
  font-size: 16px;
  cursor: pointer;
  background-color: #33b5e5;
  color: white;
  border: none;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.nav-button:hover {
  background-color: #0099cc;
}

.image-counter {
  font-size: 14px;
  margin: 0 10px;
}

.gallery-thumbnails {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}

.thumbnail {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 4px;
  cursor: pointer;
  border: 2px solid #ddd;
  padding: 2px;
  transition: all 0.3s;
}

.thumbnail:hover {
  border-color: purple;
}

.thumbnail.active {
  border-color: purple;
  box-shadow: 0 0 5px rgba(128, 0, 128, 0.5);
}

/* Footer */
.footer {
  grid-area: footer;
  background-color: #0099cc;
  color: #ffffff;
  text-align: center;
  padding: 10px;
}

/* Responsive Design */
@media (min-width: 600px) {
  .portfolio-container {
    grid-template-columns: repeat(6, 1fr);
    grid-template-areas:
      "header header header header header header"
      "menu menu menu menu menu menu"
      "content content content content content content"
      "facts facts facts facts facts facts"
      "footer footer footer footer footer footer";
  }

  .menu { grid-column: span 1; }
  .content { grid-column: span 4; }
}

@media (min-width: 768px) {
  .portfolio-container {
    grid-template-columns: repeat(6, 1fr);
    grid-template-areas:
      "header header header header header header"
      "menu menu menu menu menu menu"
      "content content content content content content"
      "facts facts facts facts facts facts"
      "footer footer footer footer footer footer";
  }

  .menu { grid-column: span 1; }
  .content { grid-column: span 4; }
  .facts { grid-column: span 1; }
}
</style>
