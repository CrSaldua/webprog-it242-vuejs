<template>
  <div class="profile-page">
    <!-- Profile Section -->
    <div class="profile-section">
      <img 
        src="https://media.licdn.com/dms/image/v2/D5603AQFpB9rCFiMUyw/profile-displayphoto-scale_200_200/B56ZqnKlsOKwAc-/0/1763741163274?e=2147483647&v=beta&t=vi0oROWu351SApec0r5CoHkB6NCjI2s3b4KE2pWIg-U" 
        alt="Cristian Profile" 
        class="profile-pic"
      >
      <h1>Im Cristian</h1>
      <div class="info">
        <p><strong>Asia Pacific College</strong></p>
        <p>Course: <strong>BSIT-242</strong></p>
        <p>IT Experience: HTML and CSS</p>
        <p>Hobbies & Interest: Playing online games with my friends</p>
        <p>Goals In Life / Dream: to be rich</p>
      </div>
    </div>

    <!-- Friends Section -->
    <h2>This is my friends And their Favorite thing</h2>
    
    <div class="container">
      <div v-for="friend in friends" :key="friend.id" class="friend-card">
        <p>{{ friend.caption }}</p>
        <img :src="friend.image" :alt="friend.alt" class="friend-pic" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PersonalProfile',
  data() {
    return {
      friends: [
        {
          id: 1,
          caption: "Dom's Favorite Hero The Milo King",
          image: "https://4.bp.blogspot.com/-BtuzkDDuVcU/WV9UpfARKNI/AAAAAAAAD0w/BbhY8uAL4KwGvIvDNO6uYrVGieFYVstLQCLcBGAs/s1600/milo%2Bman.jpg",
          alt: "Milo King"
        },
        {
          id: 2,
          caption: "Charles Favorite Movie Tangled",
          image: "https://i.pinimg.com/originals/b3/0a/ff/b30aff959dec31c10892e2c3df286fc1.png",
          alt: "Tangled"
        },
        {
          id: 3,
          caption: "Jared's Favorite Anime Character",
          image: "https://wallpapers.com/images/hd/katsuki-bakugo-my-hero-academia-iphone-hinkoepkef4nkqt2.jpg",
          alt: "Jared's Bakugo"
        },
        {
          id: 4,
          caption: "This is my friend Dom",
          image: "https://tse3.mm.bing.net/th/id/OIP.KpRPWqy3d4BwI3xbagZoBQHaHa?rs=1&pid=ImgDetMain&o=7&rm=3",
          alt: "Dom"
        },
        {
          id: 5,
          caption: "This is my friend Charles",
          image: "https://tse4.mm.bing.net/th/id/OIP.gJ-ZwX3V3r2IXmVOP93PVgAAAA?rs=1&pid=ImgDetMain&o=7&rm=3",
          alt: "Charles"
        },
        {
          id: 6,
          caption: "This is my friend Jared",
          image: "https://tse1.mm.bing.net/th/id/OIP.gbCwCpUr1rjCB6SxZuSs8AAAAA?rs=1&pid=ImgDetMain&o=7&rm=3",
          alt: "Jared"
        }
      ]
    }
  }
}
</script>

<style src="./css/personalprofile.css"></style>
