<template>
  <form @submit.prevent="submitForm">
    <div class="form-control" :class="{invalid: userNameValidate === 'invalid'}">
      <label for="user-name">Imię:</label>
      <input id="user-name" name="user-name" type="text" v-model.trim="userName" @blur="validateInput"/>
      <p v-if="userNameValidate === 'invalid'">Pole nie może być puste.</p>
    </div>
    <div class="form-control" :class="{invalid: userMailValidate === 'invalid'}">
      <label for="user-mail">Adres Email:</label>
      <input id="user-mail" name="user-mail" type="email" v-model="userMail" @blur="valuateMailInput"/>
      <p v-if="userMailValidate === 'invalid'">Pole nie może być puste.</p>
    </div>
    <div class="form-control">
      <label for="age">Wiek:</label>
      <input
        id="age"
        name="age"
        type="number"
        v-model="userAge"
        ref="ageInput"
      />
    </div>
    <div class="form-control">
      <label for="referrer">Skąd się o nas dowiedziałeś?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <option value="google">Google</option>
        <option value="facebook">Facebook</option>
        <option value="instagram">Instagram</option>
        <option value="other">inne media społecznościowe</option>
        <option value="friend">znajomi/rodzina</option>
        <option value="none">żadne z wymienionych</option>
      </select>
    </div>
    <div class="form-control">
      <h2>Co najbardziej zainteresowało Cię na naszej stronie?</h2>
      <div>
        <input id="interest-news" name="interest" type="checkbox" value="news" v-model="interest"/>
        <label class="lab" for="interest-news">nowości</label>
      </div>
      <div>
        <input id="interest-quides" name="interest" type="checkbox" value="quides" v-model="interest"/>
        <label class="lab" for="interest-quides">poradniki</label>
      </div>
      <div>
        <input id="interest-articles" name="interest" type="checkbox" value="articles" v-model="interest"/>
        <label class="lab" for="interest-articles">artykuły</label>
      </div>
      <div>
        <input id="interest-reviews" name="interest" type="checkbox" value="reviews" v-model="interest"/>
        <label class="lab" for="interest-reviews">recenzje</label>
      </div>
      <div>
        <input id="interest-courses" name="interest" type="checkbox" value="courses" v-model="interest"/>
        <label class="lab" for="interes-courses">kursy</label>
      </div>
    </div>
    <div class="form-control">
      <h2>Jak oceniasz naszą stronę? (skala 1-5):</h2>
      <div>
        <input id="rating-one" name="rating" type="radio" value="one" v-model="rating"/>
        <label class="lab" for="how-one">1</label>
      </div>
      <div>
        <input id="rating-two" name="rating" type="radio" value="two" v-model="rating"/>
        <label class="lab" for="how-two">2</label>
      </div>
      <div>
        <input id="rating-three" name="rating" type="radio" value="three" v-model="rating"/>
        <label class="lab" for="how-three">3</label>
      </div>
      <div>
        <input id="rating-four" name="rating" type="radio" value="four" v-model="rating"/>
        <label class="lab" for="how-four">4</label>
      </div>
      <div>
        <input id="rating-five" name="rating" type="radio" value="five" v-model="rating"/>
        <label class="lab" for="how-five">5</label>
      </div>
    </div>
    <div class="form-control">
      <input type="checkbox" id="confirm-terms" name="confirm-terms" v-model="confirm"/>
      <label class="confirm-terms" for="confirm-terms">Tak, uważnie zapoznałam/em się i akceptuję Regulamin Serwisu oraz Politykę Prywatności obowiązujące u Administratora.</label>
    </div>
    <div>
      <button>Zapisz</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      userName: '',
      userMail: '',
      userAge: null,
      referrer: 'google',
      interest: [],
      rating: null,
      confirm: false,
      userNameValidate: 'pending',
      userMailValidate: 'pending'
    };
  },
  methods: {
    submitForm() {
      this.userName = '';
      this.userMail = '';
      this.userAge = null;
      this.referrer = 'google';
      this.interest = [];
      this.rating = null;
      this.confirm = false
    },
    validateInput() {
      if (this.userName === '') {
        this.userNameValidate = 'invalid'
      } else {
        this.userNameValidate = 'valid'
      }
    },
    valuateMailInput() {
      if (this.userMail === '') {
        this.userMailValidate = 'invalid'
      } else {
        this.userMailValidate = 'valid'
      }
    }
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.9rem 0.2rem;
}

.form-control.invalid input {
  border-color: rgb(2, 148, 0);
}

.form-control.invalid p {
  font-size: 0.8rem;
  color: rgb(2, 148, 0);
}

label {
  font-weight: bold;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 1px;
  text-shadow: 0px 1px 2px rgb(245, 255, 244);
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
  text-shadow: 0px 1px 2px rgb(245, 255, 244);
}

input {
  padding: 7px;
  background: #f0fff4;
  border: 0;
  border-bottom: 1px solid #ddd;
}

.lab {
  text-shadow: none;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
  padding: 10px;
  background: #f0fff4;
  border-radius: 15px;
  border: 1px solid #00ce89;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

.confirm-terms {
  font-size: 0.8rem;
}

button {
  font: inherit;
  border: 1px solid #03b149;
  background-color: #00ce89;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #009d69;
  background-color: #02b378;
}
</style>
