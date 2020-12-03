<template>
  <div id="quiz">
    <h1>My Skincare Quiz</h1>
    <v-row>
      <v-col align="center" justify="center">
        <h2 v-if="loading">Loading</h2>
        <v-container
            v-if="answers"
            fluid
        >
        <v-card
            v-for="(n, index) in questions"
            :key="n.question"
            max-width="600"
            class="pa-md-4 mx-lg-auto"
        >
        <v-card-title>{{n.question}}</v-card-title>
          <v-card-actions>
          <v-radio-group>
            <v-radio
                v-for="a in n.answers"
                :key="a.answer"
                :label="a.answer"
                @change="count(index, a.value)"
            ></v-radio>
          </v-radio-group>
          </v-card-actions>
        </v-card>
        </v-container>
      </v-col>
    </v-row>
    <v-row>
      <v-col align="center" justify="center">
        <v-btn
            @click="submit">
            Submit
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Quiz',
  data() {
    return {
      answers: [0,0,0,0,0],
      questions: null,
      loading: false
    }
  },
  created () {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchQuiz()
  },
  methods: {
    fetchQuiz() {
      const self = this;
      this.loading = true;
      fetch('https://localhost:44372/quiz', {
        method: 'get',
      }).then(response => response.json())
      .then(function (data) {
        self.questions = data;
        self.loading = false;
      }).catch(function (error) {
        console.log(error);
        self.loading = false;
      });
    },
    count: function (index, value) {
      this.answers[index] = value;
    },
    submit() {
      let sum = 0;  // Variable to hold numbers as you add them up
      if (this.answers.includes(0)) {
        alert("Please answer all questions");
        return;
      }
      for (let i = 0; i < this.answers.length; i++) {
        sum += this.answers[i];  // Iterate through the array and take sum and add value of the index
        //for(let i = 0; i < this.answers.length; i++){
      }
        if (sum < 24) {
          this.skintype = "oily affordable"
        } else if (sum < 26) {
          this.skintype = "dry affordable"
        } else if (sum < 28) {
          this.skintype = "sensitive affordable"
        } else if (sum < 33) {
          this.skintype = "mature affordable"
        } else if (sum < 43) {
          this.skintype = "oily expensive"
        } else if (sum < 45) {
          this.skintype = "dry expensive"
        } else if (sum < 48) {
          this.skintype = "sensitive expensive"
        } else if (sum < 55) {
          this.skintype = "mature expensive"
        }
      this.$router.push({name: 'Results', params: {results: this.skintype + " " + sum.toString()}});
    }
    //submit() {
    // if(sum < 24)
    //   document.write("Results:" + sum + "Oily Affordable");
    // else if(sum < 26)
    //   document.write("Results:" + sum + "Dry Affordable");
    // else if(sum < 28)
    //   document.write("Results:" + sum + "Sensitive Affordable");
    // else if(sum < 33)
    //   document.write("Results:" + sum + "Aging Affordable");
    // else if(sum < 43)
    //   document.write("Results:" + sum + "Oily Expensive");
    // else if(sum < 45)
    //   document.write("Results:" + sum + "Dry Expensive");
    // else if(sum < 48)
    //   document.write("Results:" + sum + "Sensitive Expensive");
    // else if(sum < 55)
    //   document.write("Results:" + sum + "Aging Expensive");
    // },
  }
}
</script>