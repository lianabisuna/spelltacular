<template>
  <div>
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col class="d-flex child-flex"
          :cols="
            $vuetify.breakpoint.xsOnly
              ? 4
              : $vuetify.breakpoint.smAndDown
                ? 2
                : 2
          "
          @click="speak()"
          >
          <main-button color="red" icon="mdi-volume-high" caption="speak" ref="refToElement"/>
        </v-col>
        <v-col class="d-flex child-flex"
          :cols="
            $vuetify.breakpoint.xsOnly
              ? 4
              : $vuetify.breakpoint.smAndDown
                ? 2
                : 2
          "
          @click="next()"
          >
          <main-button color="green" icon="mdi-refresh" caption="next"/>
        </v-col>
      </v-row>
      <v-row justify="center">
        <v-col class="d-flex child-flex"
          :cols="
            $vuetify.breakpoint.xsOnly
              ? 12
              : $vuetify.breakpoint.smAndDown
                ? 10
                : 10
          ">
          <word v-bind:spelling="spelling" @clear="clear()" @remove="remove"/>
        </v-col>
        <v-col class="d-flex child-flex"
          :cols="
            $vuetify.breakpoint.xsOnly
              ? 4
              : $vuetify.breakpoint.smAndDown
                ? 2
                : 2
          "
          >
          <check-button v-bind:empty="(spelling.length === 0) ? true : false" @check="check()"/>
        </v-col>
      </v-row>
    </v-container>
    <v-container fluid class="pt-0">
      <v-row dense>
        <v-col
          v-for="(e,i) in alphabet"
          :key="i"
          class="d-flex child-flex"
          style="padding: 5px"
          :cols="
            $vuetify.breakpoint.xsOnly
              ? 3
              : $vuetify.breakpoint.smAndDown
                ? 2
                : 1
          "
          @click="add(e)"
        >
          <tile
            v-bind:letter="e.letter"
            v-bind:vowel="e.vowel"
            v-bind:image="e.image"
            v-bind:alt="e.alt"
          />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Tile from "@/components/Tile.vue";
import MainButton from "@/components/MainButton.vue";
import CheckButton from "@/components/CheckButton.vue";
import Word from "@/components/Word.vue";

var randomWords = require('random-words');
// var hoverSound = new Audio(require('@/assets/hover.wav'));
var clickSound = new Audio(require('@/assets/click.wav'));
var correctSound = new Audio(require('@/assets/correct.wav'));
var wrongSound = new Audio(require('@/assets/wrong.mp3'));
var removeSound = new Audio(require('@/assets/remove.wav'));
var clearSound = new Audio(require('@/assets/clear.wav'));

export default {
  name: "Home",
  components: {
    Tile,
    MainButton,
    CheckButton,
    Word
  },
  methods: {
    add(letter) {
      this.spelling.push(letter);
      clickSound.play();
    },
    clear() {
      for (var x = this.spelling.length; x > 0; x--) {
        this.spelling.pop();
      }
      clearSound.play();
    },
    remove(value) {
      this.spelling.splice(value, 1);
      removeSound.play();
    },
    speak() {
      if (this.word === '') {
        this.word = randomWords();
      }
      speechSynthesis.speak(new SpeechSynthesisUtterance(this.word));
    },
    next() {
      this.word = randomWords();
      speechSynthesis.speak(new SpeechSynthesisUtterance(this.word));
    },
    check() {
      if (this.spelling !== null) {
        var spellArray = [];
        this.spelling.forEach((v) => {
            spellArray.push(v.letter);
        });

        var spellWord = spellArray.join('').toUpperCase();
        var testWord = this.word.toUpperCase();

        if (this.spellCheck(spellWord,testWord)) {
          this.word = randomWords();
          correctSound.play();
        }
        else {
          wrongSound.play();
        }

        this.clear();
      }
    },
    spellCheck(a,b) {
      return (a === b) ? true : false;
    }
  },
  data: () => ({
    correct: false,
    word: '',
    spelling: [],
    alphabet: [
      {
        letter: "A",
        vowel: true,
        image: "https://img.icons8.com/color/48/000000/apple.png",
        alt: "apple"
      },
      {
        letter: "B",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/banana.png",
        alt: "banana"
      },
      {
        letter: "C",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/cat.png",
        alt: "cat"
      },
      {
        letter: "D",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/dog.png",
        alt: "dog"
      },
      {
        letter: "E",
        vowel: true,
        image: "https://img.icons8.com/color/48/000000/hearing.png",
        alt: "ear"
      },
      {
        letter: "F",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/frog.png",
        alt: "frog"
      },
      {
        letter: "G",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/guitar.png",
        alt: "guitar"
      },
      {
        letter: "H",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/trilby.png",
        alt: "hat"
      },
      {
        letter: "I",
        vowel: true,
        image: "https://img.icons8.com/color/48/000000/ice-cream-cone.png",
        alt: "ice-cream"
      },
      {
        letter: "J",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/jellyfish.png",
        alt: "jellyfish"
      },
      {
        letter: "K",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/key-security.png",
        alt: "key"
      },
      {
        letter: "L",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/halloween-candy.png",
        alt: "lollipop"
      },
      {
        letter: "M",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/mango.png",
        alt: "mango"
      },
      {
        letter: "N",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/nose-.png",
        alt: "nose"
      },
      {
        letter: "O",
        vowel: true,
        image: "https://img.icons8.com/color/48/000000/owl.png",
        alt: "owl"
      },
      {
        letter: "P",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/pineapple.png",
        alt: "pineapple"
      },
      {
        letter: "Q",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/queen-uk.png",
        alt: "queen"
      },
      {
        letter: "R",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/rabbit.png",
        alt: "rabbit"
      },
      {
        letter: "S",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/--sunflower.png",
        alt: "sunflower"
      },
      {
        letter: "T",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/deciduous-tree.png",
        alt: "tree"
      },
      {
        letter: "U",
        vowel: true,
        image: "https://img.icons8.com/color/48/000000/umbrella.png",
        alt: "umbrella"
      },
      {
        letter: "V",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/pottery.png",
        alt: "vase"
      },
      {
        letter: "W",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/watermelon.png",
        alt: "watermelon"
      },
      {
        letter: "X",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/xylophone.png",
        alt: "xylophone"
      },
      {
        letter: "Y",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/guru.png",
        alt: "yoga"
      },
      {
        letter: "Z",
        vowel: false,
        image: "https://img.icons8.com/color/48/000000/zombie.png",
        alt: "zombie"
      }
    ]
  })
};
</script>
