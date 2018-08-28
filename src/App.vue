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
          <el-radio label="f2">Get so anxious I have trouble focussing</el-radio>
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
        desc: 'embodies chaos, unrelentingly savage',
      },
      infj: {
        name: 'Fantastic Fox',
        desc: 'clever, creative, loves family',
      },
      enfp: {
        name: 'Hooded Fox',
        desc: 'mischeivous, strong sense of justice',
      },
      esfp: {
        name: 'Fox Royale',
        desc: 'loves parties, impressed easily',
      },
      esfj: {
        name: 'Fox Toddy',
        desc: 'tame, loving, accepting',
      },
      istp: {
        name: 'Set Fox',
        desc: 'likes water, competitive, stubborn',
      },
      entj: {
        name: 'Cadmean Vixen',
        desc: 'giant, vicious, astral',
      },
      entp: {
        name: 'Kuma Lisa',
        desc: 'godmother, smart, helpful',
      },
      enfj: {
        name: 'Finnish Fox',
        desc: 'Troll, loyal',
      },
      infp: {
        name: 'Tame Fox',
        desc: 'Gregarious, introverted, insightful',
      },
      isfp: {
        name: 'Ninhursag\'s Fox',
        desc: 'messenger, comfortor'
      },
      intp: {
        name: 'Kitsune',
        desc: 'Love inari productive, faithful, loyal, demands respect',
      },
      istj: {
        name: 'Gumiho',
        desc: 'Contains a bead of knowledge, always fox-like'
      },
      estp: {
        name: 'Moche Fox',
        desc: 'Mental worrior, between two worlds'
      },
      estj: {
        name: 'Lo Rainard',
        desc: 'The lord',
      },
      intj: {
        name: 'Huli Jing',
        desc: 'smart sorceror who trains hard, between dark and light'
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
