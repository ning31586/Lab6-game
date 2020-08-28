<template>
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:500px" :src="aplayer.image" />
        </p>
      </div>
      <div class="row">
      <div class="col"></div>
      <div class="col"></div>
    </div>
      <div class="col-sm">
        <div class="row">
          <div class="col">
            <button class="btn btn-primary" @click="start()">เริ่ม</button>
          </div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()">โจมตี</button>
          </div>
          <div class="col">
            <button class="btn btn-light" @click="reset()">เล่นอีกครั้ง</button>
          </div>
          <br />
          <img src="https://www.nicepng.com/png/full/20-200345_street-fighter-vs-png-vs-street-fighter-logo.png"
            width="100%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="amonster.hp <= 0"><FONT COLOR=black>คุณชนะ!</FONT></div>
              <div v-else-if="aplayer.hp <= 0"><FONT COLOR=black>คุณแพ้!</FONT></div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p><img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" /></p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p><img style="width:90%" :src="amonster.image" /></p>
      </div>
    </div>
    <hr />
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      hp1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        {name: "Shirokuma",hp: 500,image:
            "https://image.dek-d.com/26/3204206/113424503",
        },
        {name: "Penguin",hp: 450,image:
            "https://image.dek-d.com/26/3204206/113424495",
        },
        {name: "Neko",hp: 400,image:
            "https://image.dek-d.com/26/3204206/113424489",
        },
        {name: "Tonkatsu",hp: 350,image:
            "https://image.dek-d.com/26/3204206/113424514",
        },
        {name: "Tokage",hp: 300,image: 
            "https://123emoji.com/wp-content/uploads/2017/08/sticker-99.png",
        },
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        {name: "My Melody",hp: 400,image:
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_my_melody.png",
        },
        {name: "Pompompurin",hp: 450,image:
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_pompompurin.png",
        },
        {name: "Gudetame",hp: 500,image:
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_gudetame.png",
        },
        {name: "Little Twin Stars",hp: 550,image: 
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_little_twin_star.png",
        },
        {name: "Bad Batdz-Maru",hp: 600,image: 
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_badtz_maru.png",
        },
        {name: "Hello Kitty",hp: 650,image: 
            "https://d1j36w0bax18n0.cloudfront.net/media/wysiwyg/sanrio/icon_kitty.png",
        },
      ],
      player_max: "",
      monster_max: "",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 5) - 1];
      this.amonster = this.monster[this.randomno(1, 6) - 1];
    },
    attack: function () {
      this.player_max = Math.floor(Math.random() * 15 + 3);
      this.amonster.hp = this.amonster.hp - this.player_max;
      this.monster_max = Math.floor(Math.random() * 10 + 3);
      this.aplayer.hp = this.aplayer.hp - this.monster_max;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 500%;
  color: aliceblue;
}
</style>