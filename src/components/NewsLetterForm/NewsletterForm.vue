<script setup></script>

<template>
  <article class="newsletter-form">
    <img src="./../../assets/images/illustration-sign-up-mobile.svg" />
    <div class="form-content">
      <h2>Stay updated!</h2>
      <p>Join 60,000 product managers receiving monthly updates on:</p>
      <ul class="form-checklist">
        <li>Product discovery and building what matters</li>
        <li>Measuring to ensure updates are a success</li>
        <li>And much more!And much more!And much more!</li>
      </ul>
      <form>
        <div class="form-item">
          <label>Email address</label>
          <input type="email" placeholder="email@company.com" />
        </div>

        <button class="submit-button" type="button">
          Subscribe to monthly newsletter
        </button>
      </form>
    </div>
  </article>
</template>

<style scoped>
.newsletter-form {
  display: flex;
  flex-direction: column;
  font-weight: var(--weight-normal);
  color: var(--dark-grey);
  min-width: 375px;
}

.form-content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  padding: 2rem;
}

.form-content h2 {
  color: var(--dark-grey);
  font-size: 2.5rem;
  font-weight: var(--weight-bold);
}

.form-content p {
  font-size: 1rem;
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
  content: '';
  display: block;
  width: 24px;
  height: 24px;
  background-image: url(./../../assets/images/icon-success.svg);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-item {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-item label {
  font-size: 0.75rem;
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

.submit-button {
  background: var(--dark-grey);
  color: var(--white);
  padding: 1rem 2rem;
  border: 0;
  border-radius: 0.5rem;
}
</style>
