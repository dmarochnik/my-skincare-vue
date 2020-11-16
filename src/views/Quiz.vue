<template>
  <div id="quiz">
    <h1>My Skincare Quiz</h1>
    <v-row>
      <v-col align="center" justify="center">
        <v-container fluid>
        <v-card
            v-for="(n, index) in questions"
            :key="n.question.text"
            max-width="600"
            class="pa-md-4 mx-lg-auto"
        >
        <v-card-title>{{n.question.text}}</v-card-title>
          <v-card-actions>
          <v-radio-group>
            <v-radio
                v-for="a in n.question.answers"
                :key="a.text"
                :label="a.text"
                @change="count(index, a.val)"
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
      questions: [
        {
          question: {
            text: "1. How would you describe your skin?",
            answers: [
              {
                text: "Oily",
                val: 1
              },
              {
                text: "Dry",
                val: 2
              },
              {
                text: "Sensitive",
                val: 3
              },
              {
                text: "Aging",
                val: 4
              }
            ]
          },
        },
        {
          question: {
            text: "2. What is your number one skin goal?",
            answers: [
              {
                text: "Get rid of blemishes and blackheads",
                val: 1
              },
              {
                text: "Get rid of flaky, dry skin",
                val: 2
              },
              {
                text: "Find products that don't irritate my skin",
                val: 3
              },
              {
                text: "Reduce fine lines and wrinkles",
                val: 4
              }
            ]
          },
        },
        {
          question: {
            text: "3. Which of the following is most important to you?",
            answers: [
              {
                text: "Keeping my skincare routine short and simple.",
                val: 10
              },
              {
                text: "I need my skincare routine to be inexpensive.",
                val: 10
              },
              {
                text: "I want the latest, top of the line products.",
                val: 20
              },
              {
                text: "Finding the right combination of products, even if it means spending extra time on my routine.",
                val: 20
              },
            ]
          },
        },
        {
          question: {
            text: "4. How old are you?",
            answers: [
              {
                text: "18-24",
                val: 1
              },
              {
                text: "25-34",
                val: 1
              },
              {
                text: "35-44",
                val: 4
              },
              {
                text: "44+",
                val: 4
              }
            ]
          },
        },
        {
          question: {
            text: "5. Which of the following brands do you prefer?",
            answers: [
              {
                text: "Neutrogena",
                val: 10
              },
              {
                text: "Proactiv",
                val: 10
              },
              {
                text: "Murad",
                val: 20
              },
              {
                text: "Clinique",
                val: 20
              }
            ]
          },
        }
      ]
    }
  },
  methods: {
    count: function (index, value){
      alert("for question" + index + "your answer value is" + value)
    },
    submit() {
      let nums = ('1', '2', '3', '4', '5'),
          num = 0;

      for (let i = 0; i < nums.length; i++) {
        num += +nums[i];
      }
      document.write("Total:" + num);
      const self = this;

      self.$router.push('/results');
    },
  }
}
</script>