<template>
  <ion-page>
    <ion-content :fullscreen="true">


  <div class="app-container">

    <!-- Main conversation card -->
    <div class="conversation-card">

      <!-- App icon -->
      <div class="question-icon">
        💬
      </div>

      <!-- Question -->
      <div class="question-box">

        <p class="person-label">
          Someone asked:
        </p>

        <h1>
          Tapos ka na dun sa act
          kay Ma'am Malou?
        </h1>

      </div>

      <!-- Answer button -->
      <div
        v-if="!hasAnswered"
        class="answer-buttons"
      >

        <ion-button
          expand="block"
          @click="answerNo"
        >
          Hindi pa
        </ion-button>

      </div>

      <!-- Response -->
      <div
        v-if="hasAnswered"
        class="response-section"
      >

        <div class="response-label">
          Your answer:
        </div>

        <div class="response-bubble">

          <p>
            {{ response }}
          </p>

        </div>

        <!-- Reset the conversation -->
        <ion-button
          fill="clear"
          @click="resetConversation"
        >
          ↻ Ask Again
        </ion-button>

      </div>

    </div>

  </div>

</ion-content>


  </ion-page>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonContent,
  IonButton,
} from "@ionic/vue";

import { ref } from "vue";

/*
  Controls whether the user
  has already answered.
*/
const hasAnswered = ref(false);

/*
  Stores the response
  displayed on the screen.
*/
const response = ref("");

/*
  Called when the user clicks
  the "Hindi pa" button.
*/
const answerNo = () => {

  response.value =
    "Hindi pa, bakit mo naitanong?haha";

  hasAnswered.value = true;
};

/*
  Resets the application
  to its initial state.
*/
const resetConversation = () => {

  hasAnswered.value = false;

  response.value = "";
};
</script>

<style scoped>

/* Full-screen application background */
.app-container {
  min-height: 100%;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 20px;

  background:
    linear-gradient(
      135deg,
      #eef4ff,
      #f7f2ff
    );
}

/* Main conversation card */
.conversation-card {
  width: 100%;
  max-width: 420px;

  padding: 30px 25px;

  text-align: center;

  border-radius: 25px;

  background: white;

  box-shadow:
    0 12px 35px
    rgba(0, 0, 0, 0.12);

  animation:
    cardAppear
    0.6s
    ease;
}

/* Question icon */
.question-icon {
  font-size: 60px;

  margin-bottom: 15px;

  animation:
    float
    2.5s
    ease-in-out
    infinite;
}

/* Question container */
.question-box {
  padding: 20px;

  margin-bottom: 25px;

  border-radius: 18px;

  background:
    #f3f6ff;
}

/* Small label */
.person-label {
  margin: 0 0 10px;

  font-size: 14px;

  color: #777;
}

/* Main question */
h1 {
  margin: 0;

  font-size: 24px;

  line-height: 1.4;

  color: #333;
}

/* Answer button container */
.answer-buttons {
  display: flex;

  flex-direction: column;

  gap: 12px;
}

/* Response section */
.response-section {
  animation:
    fadeIn
    0.5s
    ease;
}

/* Response label */
.response-label {
  margin-bottom: 10px;

  font-size: 14px;

  color: #777;
}

/* Chat-style response bubble */
.response-bubble {
  padding: 18px;

  margin-bottom: 15px;

  border-radius:
    20px
    20px
    5px
    20px;

  background:
    #e8f0ff;

  text-align: left;
}

/* Response text */
.response-bubble p {
  margin: 0;

  font-size: 18px;

  line-height: 1.5;

  color: #333;
}

/* Card entrance animation */
@keyframes cardAppear {

  from {
    opacity: 0;

    transform:
      translateY(25px);
  }

  to {
    opacity: 1;

    transform:
      translateY(0);
  }

}

/* Floating icon animation */
@keyframes float {

  0%,
  100% {
    transform:
      translateY(0);
  }

  50% {
    transform:
      translateY(-8px);
  }

}

/* Response appearance animation */
@keyframes fadeIn {

  from {
    opacity: 0;

    transform:
      scale(0.95);
  }

  to {
    opacity: 1;

    transform:
      scale(1);
  }

}

</style>
