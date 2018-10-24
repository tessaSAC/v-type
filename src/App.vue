<template>
<div id="app">
  <el-card class="formCard">
    <div slot="header" class="clearfix">
      <span>What's your v-type?</span>
    </div>


    <el-form
      v-if="!submitted"
      ref="form"
      :model="form"
      label-position="top"
    >
      <el-form-item label="My favorite type of movie is">
        <el-radio-group v-model="form.q1">
          <el-radio label="f1">A feel good movie</el-radio>
          <el-radio label="t1">One that makes me think</el-radio>
          <el-radio label="n1">A movie about witchcraft</el-radio>
          <el-radio label="j1">One that gives me a new outlook on life</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="On a Saturday night I prefer to">
        <el-radio-group v-model="form.q2">
          <el-radio label="i2">Read a quiet book over tea</el-radio>
          <el-radio label="e2">Hang out in da club</el-radio>
          <el-radio label="e1">Chill in a bar</el-radio>
          <el-radio label="i1">Meet a friend for a nice dinner</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="When I’m giving advice the first thing I ask is">
        <el-radio-group v-model="form.q3">
          <el-radio label="s1">What are your next steps?</el-radio>
          <el-radio label="n2">How do you feel?</el-radio>
          <el-radio label="s2">What happened?</el-radio>
          <el-radio label="n1">What do you want to do?</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="My favorite front-end framework du jour is">
        <el-radio-group v-model="form.q4">
          <el-radio label="j1">Angular</el-radio>
          <el-radio label="n1">Vue.js</el-radio>
          <el-radio label="f1">Wix</el-radio>
          <el-radio label="t1">React</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="Something I’d like to get better at is">
        <el-radio-group v-model="form.q5">
          <el-radio label="n1">Setting priorities</el-radio>
          <el-radio label="t1">Doing things I love more often</el-radio>
          <el-radio label="j1">Letting loose</el-radio>
          <el-radio label="f1">Spending time with friends or family</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="When I get stuck on a hard problem, I">
        <el-radio-group v-model="form.q6">
          <el-radio label="t2">Try to look at the problem from another perspective</el-radio>
          <el-radio label="f1">Take a walk or draw for a few minutes</el-radio>
          <el-radio label="t1">Go over the problem from the beginning</el-radio>
          <el-radio label="f2">Get so anxious I have trouble focusing</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="When I’m planning to give a tech talk, I">
        <el-radio-group v-model="form.q7">
          <el-radio label="j2">Plan down to the second and memorize my talk</el-radio>
          <el-radio label="p1">Make an outline and fill in the blanks the day of</el-radio>
          <el-radio label="j1">Create a slideshow and prepare some notecards</el-radio>
          <el-radio label="p2">Wing some live code</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="My friends would describe me as">
        <el-radio-group v-model="form.q8">
          <el-radio label="n1">Thoughtful</el-radio>
          <el-radio label="t1">Smart</el-radio>
          <el-radio label="f1">Affectionate</el-radio>
          <el-radio label="j1">Clever</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="If I could solve any problem it would be">
        <el-radio-group v-model="form.q9">
          <el-radio label="n1">Miscommunication</el-radio>
          <el-radio label="j1">Bureaucratic inefficiency</el-radio>
          <el-radio label="f1">Broken marriages</el-radio>
          <el-radio label="t1">The education system</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="I pull pranks">
        <el-radio-group v-model="form.q10">
          <el-radio label="e2">Often</el-radio>
          <el-radio label="e1">Sometimes</el-radio>
          <el-radio label="i1">Rarely</el-radio>
          <el-radio label="i2">Never</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="My favorite food is">
        <el-radio-group v-model="form.q11">
          <el-radio label="n1">Something with an interesting texture or quality crunch</el-radio>
          <el-radio label="f1">Something sweet or fatty</el-radio>
          <el-radio label="t1">Something nutritious</el-radio>
          <el-radio label="j1">Something I don’t get to eat often</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="If I were a planeteer my power would be">
        <el-radio-group v-model="form.q12">
          <el-radio label="j1">Earth</el-radio>
          <el-radio label="n1">Fire</el-radio>
          <el-radio label="t1">Water</el-radio>
          <el-radio label="f1">Heart</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item label="I’m here because">
        <el-radio-group v-model="form.q13">
          <el-radio label="n1">It seemed like fun</el-radio>
          <el-radio label="t1">I want to learn something new</el-radio>
          <el-radio label="j1">I want to expand my repertoire</el-radio>
          <el-radio label="e1">I want to meet new people</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="onSubmit">🦊🦊🦊 HOW FOXY AM I? 🦊🦊🦊</el-button>
      </el-form-item>
    </el-form>

    <div v-else>
      <h1>You are a {{ foxType }}</h1>
      <p>{{ foxDesc }}</p>
    </div>
  </el-card>
</div>
</template>

<script>
export default {
  data: _ => ({
    attributes: {
      e: 0,
      i: 0,

      s: 0,
      n: 0,

      t: 0,
      f: 0,

      j: 0,
      p: 0,
    },

    form: {
      q1: '',
      q2: '',
      q3: '',
      q4: '',
      q5: '',
      q6: '',
      q7: '',
      q8: '',
      q9: '',
      q10: '',
      q11: '',
      q12: '',
      q13: '',
    },

    foxes: {
      isfj: {
        name: 'Pale Fox',
        desc: 'Your friends would describe you as warm and considerate. Although you value harmony and are sensitive to others\' feelings, you can sometimes feel chaotic inside. You have a natural tendency towards hard work and savage perfectionism.',
      },
      infj: {
        name: 'Fantastic Fox',
        desc: 'You are a clever, creative, and imaginative idealist who possesses a difference in the way you see the world. You are gentle and caring and value family, whether that means by blood or by choice.',
      },
      enfp: {
        name: 'Hooded Fox',
        desc: 'You love standing apart from the crowd and hate being labeled or put inside a box (yes you know it rhymes). While you enjoy company, you also get bored easily and can be mischievous at times. You have a strong sense of justice.',
      },
      esfp: {
        name: 'Fox Royale',
        desc: 'You love being around people! Are you the life of the party?! While you enjoy being the center of attention, you have strong interpersonal skills and tend to notice and appreciate others; you are also warm and generously compassionate.',
      },
      esfj: {
        name: 'Fox Toddy',
        desc: 'You love interacting with others and being in the spotlight. Everyone is happy to have you around! People are attracted to you because of your good listening skills and your loving and accepting nature.',
      },
      istp: {
        name: 'Set Fox',
        desc: 'You are a bit mysterious! Like water, your personality isn\'t confined to one extreme -- you can be rational at times and spontaneous at others. You can be funny and insightful, but also competitive and stubborn. However, fairness and equality are important to you.',
      },
      entj: {
        name: 'Cadmean Vixen',
        desc: 'As a fox who tends to tenaciously attack problems with both logic and emotion, you seem to have a natural gift for considering options and making considered decisions. You love being with people but find it challenging to get close to people. You may feel as though you\'re destined for greatness, as you have a special connection with the stars.',
      },
      entp: {
        name: 'Kuma Lisa',
        desc: 'You love to shred apart the status quo and reevaluate its corpse with a fresh eye. Although you are intelligent and love helping people, you also love to question society and whether it\'s really for you.',
      },
      enfj: {
        name: 'Finnish Fox',
        desc: 'You love people and are charismatic and principled. You mainly act on intuition and feeling. Although you sometimes troll people for fun, you also tend towards loyalty and genuine kindness.',
      },
      infp: {
        name: 'Tame Fox',
        desc: 'You can be both gregarious and introverted. When you first meet someone, you prefer to not reveal much about yourself. However you are also insightful about people and are driven to make the world a better place.',
      },
      isfp: {
        name: 'Ninhursag\'s Fox',
        desc: 'Aesthetics are important to you, as are pushing boundaries and convention. You are comfortable in your own skin, which makes you a compassionate and understanding listener who friends trust for advice and reassurance.'
      },
      intp: {
        name: 'Kitsune',
        desc: 'You love patterns and have a tendency to be detail-oriented. Despite that, you often share ideas before they are fully-formed, but you don\'t let that stop you from methodically working through your thoughts. Respect and tofu are important to you, and you make a faithful and loyal companion.',
      },
      istj: {
        name: 'Gumiho',
        desc: 'You are a logical and organized hard worker who values tradition, knowledge, and honesty. Although you may be patient and reserved, you cannot always hide your true fox-like nature.'
      },
      estp: {
        name: 'Moche Fox',
        desc: 'You may often feel as if you are between two worlds, as you are driven by both emotion and logic. Brave and passionate, you ask for forgiveness rather than permission. Although you chafe at structure, you love a good puzzle.'
      },
      estj: {
        name: 'Lo Rainard',
        desc: 'You always strive to work towards what you believe is good and right above all else and put effort into being a good role model. You love bringing communities together and upholding values you find important.',
      },
      intj: {
        name: 'Huli Jing',
        desc: 'You are self-sufficient and comfortable working alone. You are fascinated by ideas and theories, and value competence. You trust your gut instinct and stand on the liminal edge between dark and light.'
      }
    },

    foxType: '',
    foxDesc: '',

    submitted: false,
  }),

  methods: {
    compare(a, b) {
      return this.attributes[a] > this.attributes[b]
        ? a
        : this.attributes[b] > this.attributes[a]
          ? b
          : this.getRandoNum()
            ? a
            : b
    },

    findType() {
      const type = [
        this.compare('e', 'i'),
        this.compare('s', 'n'),
        this.compare('t', 'f'),
        this.compare('j', 'p'),
      ].join('')

      this.foxType = this.foxes[type].name
      this.foxDesc = this.foxes[type].desc
    },

    onSubmit() {
      // tally scores
      for (const question in this.form) {
        const [attribute, score] = this.form[question].split('')
        this.attributes[attribute] += +score
      }

      this.findType()

      this.submitted = true
    },

    getRandoNum() {
      return Math.floor(Math.random() * Math.floor(2))
    },
  },
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: space-around;
}

.formCard {
  width: 50vw;
  min-width: 500px;
}

.el-radio-group {
  display: flex;
  flex-direction: column;
  padding: 0 2rem;
  align-items: flex-start;

  .el-radio, +el-radio {
    margin-left: 2rem;
  }
}
</style>
