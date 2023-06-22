<script>
import { FormKit } from '@formkit/vue';
export default {
  mounted() {
    console.log(this.email);
  },
  data() {
    return {
      email: '',
      successful: false,
      errors: {},
      email_regex: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
    };
  },
  methods: {
    dismissMessage() {
      this.successful = false;
    },
    submitForm() {
      let emailErrors = '';
      if (!this.email) {
        emailErrors = 'Email is required';
      } else if (!this.email_regex.test(this.email)) {
        emailErrors = 'Valid email required';
      } else {
        emailErrors = '';
      }

      this.errors = {
        email: emailErrors,
      };

      this.successful = this.errors.email.length === 0;
      console.log(!this.email_regex.test(this.email), this.errors);
    },
  },
  components: { FormKit },
};
</script>

<template>
  <article v-if="!successful" class="newsletter-form">
    <picture>
      <source
        media="(min-width:50em)"
        srcset="./../../assets/images/illustration-sign-up-desktop.svg"
      />
      <img src="./../../assets/images/illustration-sign-up-mobile.svg" />
    </picture>

    <div class="form-content">
      <h2 class="heading">Stay updated!</h2>
      <p>Join 60,000 product managers receiving monthly updates on:</p>
      <ul class="form-checklist">
        <li>Product discovery and building what matters</li>
        <li>Measuring to ensure updates are a success</li>
        <li>And much more!</li>
      </ul>
      <form
        @submit.prevent="submitForm"
        :data-error="this.errors.email && this?.errors?.email != 0"
      >
        <div class="form-item">
          <div class="form-item-header">
            <label for="email">Email address</label>
            <span class="form-error">{{ this.errors.email }}</span>
          </div>
          <input v-model="email" placeholder="email@company.com" />
        </div>
        <button class="button" type="submit">
          Subscribe to monthly newsletter
        </button>
      </form>
    </div>
  </article>

  <article v-if="successful" class="success-message">
    <img src="./../../assets/images/icon-success.svg" alt="success icon" />
    <h1 class="heading">Thanks for subscribing</h1>
    <p>
      A confirmation email has been sent to
      <strong>ash@loremcompany.com.</strong> Please open it and click the button
      inside to confirm your subscription.
    </p>
    <button @click.prevent="dismissMessage" class="button">
      Dismiss message
    </button>
  </article>
</template>

<style scoped>
.newsletter-form {
  font-weight: var(--weight-normal);
  color: var(--dark-grey);
  background-color: var(--white);
  display: flex;
  flex-direction: column;
  min-width: 22em;
  margin: 1rem;
  opacity: 1;
  border-radius: 2rem;
  overflow: hidden;
  max-width: 30em;
}

picture img {
  width: 100%;
  height: auto;
}

.form-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: clamp(2rem, 10vw, 3rem);
}

.heading {
  color: var(--dark-grey);
  font-size: var(--font-large);
  font-weight: var(--weight-bold);
  line-height: 1.2;
}

.form-content h2 {
  color: var(--dark-grey);
  font-size: var(--font-large);
  font-weight: var(--weight-bold);
}

.form-content p {
  font-size: var(--font-medium);
}

.form-checklist {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-checklist li {
  display: flex;
  gap: 1rem;
  align-items: start;
}

.form-checklist li::before {
  content: url(./../../assets/images/icon-success.svg);
  width: 24px;
  height: 24px;
}

form[data-error='false'] input {
  background-color: var(--white);
}

form[data-error='true'] input {
  background-color: var(--tomato-light);
}

form[data-error='true'] input::placeholder {
  color: var(--pink);
}

.form-item {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-item-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.form-error {
  color: var(--tomato);
  font-size: var(--font-small);
  font-weight: var(--weight-bold);
}

.form-item label {
  font-size: var(--font-small);
  font-weight: var(--weight-bold);
  color: var(--charcoal-grey);
}

.form-item input {
  padding: 1rem;
  border: 1px solid var(--grey);
  border-radius: 0.5rem;
}

.form-item input::placeholder {
  color: var(--grey);
}

.button {
  margin-top: 1rem;
  cursor: pointer;
  background: var(--dark-grey);
  color: var(--white);
  padding: 1rem 2rem;
  border: 0;
  width: 100%;
  border-radius: 0.5rem;
}

button:hover {
  background: linear-gradient(to right, var(--pink), var(--tomato));
}

.success-message {
  display: flex;
  padding: 1.5rem;
  flex-direction: column;
  padding-top: 8rem;
  gap: 2rem;
  height: 100vh;
  max-width: 28rem;
  font-weight: var(--weight-normal);
  color: var(--dark-grey);
  background-color: var(--white);
  margin: 1rem auto;
  border-radius: 0;
  opacity: 1;
  transition: opacity 500s ease-in;
}

.success-message img {
  width: 75px;
  height: 75px;
}

.success-message .button {
  margin-top: auto;
}

@media screen and (min-width: 50em) {
  .newsletter-form {
    flex-direction: row-reverse;
    max-width: 60em;
  }
  .newsletter-form > * {
    flex: 1;
  }

  picture img {
    height: 100%;
    object-fit: cover;
    padding: 1rem;
    border-radius: 2rem;
  }

  .form-content {
    margin-block: auto;
  }

  .success-message {
    padding: 2rem;
    border-radius: 2rem;
    height: auto;
  }

  .success-message .button {
    margin: 0;
  }
}

.hidden {
  opacity: 0;
  display: none;
}
</style>
