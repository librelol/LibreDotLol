<template>
    <v-container>
      <v-card>
        <v-card-title>
          <h2>Threat Model Survey</h2>
        </v-card-title>
        <v-card-subtitle>
          <p>Answer the following questions to get recommendations on what software you probably should use</p>
          <p>As a reminder this survey is currently in Alpha and might not be entirely correct</p>
        </v-card-subtitle>
        <v-card-text>
          <v-form v-model="valid" ref="form">
            <v-list>
              <v-list-item v-if="currentQuestion < questions.length">
                <v-list-item-content>
                  <v-list-item-title class="question-title">{{ questions[currentQuestion].text }}</v-list-item-title>
                  <v-radio-group v-model="selectedAnswer" :rules="[v => !!v || 'Required']">
                    <v-radio
                      v-for="(option, optIndex) in questions[currentQuestion].options"
                      :key="optIndex"
                      :label="option.label"
                      :value="option"
                      class="radio-option"
                    />
                  </v-radio-group>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-btn @click="nextQuestion" :disabled="!valid || selectedAnswer === null" color="primary">
              {{ currentQuestion < questions.length - 1 ? 'Next' : 'Submit' }}
            </v-btn>
          </v-form>
  
          <v-alert v-if="submitted" type="success" class="results-alert">
            <div>
              <h3>Your Results:</h3>
              <p><strong>Total Points:</strong> {{ totalPoints }}</p>
              <p>Points aren't a score its just a digit that's associated with your option to represent the overall security you need</p>
              <v-divider></v-divider>
              <p>{{ recommendation }}</p>
              <v-divider></v-divider>
              <div v-for="(question, index) in questions" :key="index" class="result-item">
                <strong>{{ question.text }}</strong><br />
                <span>Your answer: <strong>{{ answers[index].label }}</strong></span><br />
                <span>Response: <em>{{ answers[index].response }}</em></span>
              </div>
              <v-btn @click="downloadResults" color="primary">Download Results</v-btn>
            </div>
          </v-alert>
        </v-card-text>
      </v-card>
    </v-container>
  </template>
  
  <script>
  import questions from '@/questions.json'; // Adjust the path as necessary
  
  export default {
    data() {
      return {
        valid: false,
        submitted: false,
        currentQuestion: 0,
        questions: questions,
        selectedAnswer: null,
        answers: [],
        totalPoints: 0,
        recommendation: '',
      };
    },
    methods: {
      nextQuestion() {
        if (this.currentQuestion < this.questions.length) {
          if (this.selectedAnswer) {
            this.answers[this.currentQuestion] = this.selectedAnswer;
            this.totalPoints += this.selectedAnswer.points;
          }
  
          this.currentQuestion++;
          this.selectedAnswer = null;
  
          if (this.currentQuestion === this.questions.length) {
            this.submitted = true;
            this.recommendation = this.getRecommendation(this.totalPoints);
          }
        }
      },
      getRecommendation(points) {
        if (points <= 5) {
          return "Consider using basic security applications.";
        } else if (points <= 10) {
          return "Implement moderate security measures and applications.";
        } else {
          return "Highly recommended to use advanced security applications.";
        }
      },
      downloadResults() {
        const results = this.generateResultsText();
        const blob = new Blob([results], { type: 'text/plain' });
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = 'threat_model_survey.txt';
        link.click();
      },
      generateResultsText() {
        let results = `Your Threat Model Survey Results:\n\nTotal Points: ${this.totalPoints}\n${this.recommendation}\n\n`;
        this.questions.forEach((question, index) => {
          results += `Question: ${question.text}\nYour answer: ${this.answers[index].label}\nResponse: ${this.answers[index].response}\n\n`;
        });
        return results;
      }
    },
  };
  </script>
  
  <style scoped>
  .question-title {
    font-weight: bold;
    font-size: 1.2em;
    margin-bottom: 10px;
  }
  
  .radio-option {
    margin: 5px 0;
  }
  
  .results-alert {
    margin-top: 20px;
    padding: 15px;
  }
  
  .result-item {
    margin-bottom: 15px;
    border-bottom: 1px solid #ccc;
    padding-bottom: 10px;
  }
  </style>
  