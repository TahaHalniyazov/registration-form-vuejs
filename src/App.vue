<template>
  <div class="form-container">
    <form  class="form" novalidate>
      <div class="forms">
        <!-- Атрибуты формы -->
        <div>
          <div class="form-group">
            <label for="surname">Фамилия<span>*</span></label>
            <input type="text" @blur="$v.formReg.surname.$touch()"  id="surname" v-model="formReg.surname" >
            <div v-if="$v.formReg.surname.$dirty">
              <div v-if="!$v.formReg.surname.required" class="invalid">Поле обязательно для заполнения</div>
              <div v-if="!$v.formReg.surname.alpha" class="invalid">В поле не должно содержаться цифры<br> и другие символы</div>
            </div>
          </div>
          <div class="form-group">
            <label for="name">Имя<span>*</span></label>
            <input type="text" @blur="$v.formReg.name.$touch()" id="name" v-model="formReg.name" required>
            <div v-if="$v.formReg.name.$dirty">
              <div v-if="!$v.formReg.name.required" class="invalid">Поле обязательно для заполнения</div>
              <div v-if="!$v.formReg.name.alpha" class="invalid">В поле не должно содержаться цифры<br> и другие символы</div>
            </div>
          </div>
          <div class="form-group">
            <label for="patronymic">Отчество</label>
            <input type="text" id="patronymic" v-model="formReg.patronymic">
          </div>
          <div class="form-group">
            <label for="dob">Дата рождения<span>*</span></label>
            <input type="date" @blur="$v.formReg.dob.$touch()" id="dob" v-model="formReg.dob" >
            <div v-if="$v.formReg.dob.$dirty">
              <div v-if="!$v.formReg.dob.required" class="invalid">Поле обязательно для заполнения</div>
            </div>  
          </div>
          <div class="form-group">
            <label for="phone">Номер телефона<span>*</span></label>
            <input type="tel" @blur="$v.formReg.phone.$touch()" id="phone" v-model="formReg.phone" pattern="[0-9]{11}" >
            <div v-if="$v.formReg.phone.$dirty">
              <div v-if="!$v.formReg.phone.required" class="invalid">Поле обязательно для заполнения</div>
              <div v-else-if="!$v.formReg.phone.numeric || !$v.formReg.phone.minLength || !$v.formReg.phone.maxLength || !$v.formReg.phone.startsWithSeven" class="invalid">Введите 11 цифр. (Начинается с 7)</div>
            </div>
          </div>
          <div class="form-group">
            <label for="gender">Пол</label>
            <select id="gender" v-model="formReg.gender">
              <option value="male">Мужской</option>
              <option value="female">Женский</option>
            </select>
          </div>
          <div class="form-group">
            <label for="customerGroup">Группа клиентов<span>*</span></label>
            <select id="customerGroup" @blur="$v.formReg.customerGroup.$touch()" v-model="formReg.customerGroup" multiple >
              <option value="VIP">VIP</option>
              <option value="problematic">Проблемные</option>
              <option value="OMS">ОМС</option>
            </select>
            <div v-if="$v.formReg.customerGroup.$dirty">
              <div v-if="!$v.formReg.customerGroup.required" class="invalid">Поле обязательно для заполнения</div>
            </div>
          </div>
          <div class="form-group">
            <label for="doctor">Лечащий врач</label>
            <select id="doctor" v-model="formReg.doctor">
              <option value="Ivanov">Иванов</option>
              <option value="Zakharov">Захаров</option>
              <option value="Chernysheva">Чернышева</option>
            </select>
          </div>
          <div class="form-group">
            <input type="checkbox" id="noSMS" v-model="formReg.noSMS">
            <label for="noSMS">Не отправлять СМС</label>
          </div>
        </div>
        <!-- Адрес -->
        <div>
          <div class="form-group">
            <label for="zip">Индекс</label>
            <input type="text" id="zip" v-model="formReg.zip">
          </div>
          <div class="form-group">
            <label for="country">Страна</label>
            <input type="text" id="country" v-model="formReg.country">
          </div>
          <div class="form-group">
            <label for="region">Область</label>
            <input type="text" id="region" v-model="formReg.region">
          </div>
          <div class="form-group">
            <label for="city">Город<span>*</span></label>
            <input type="text" @blur="$v.formReg.city.$touch()" id="city" v-model="formReg.city" >
            <div v-if="$v.formReg.city.$dirty">
              <div v-if="!$v.formReg.city.required" class="invalid">Поле обязательно для заполнения</div>
              <div v-if="!$v.formReg.city.alpha" class="invalid">В поле не должно содержаться цифры<br> и другие символы</div>
            </div> 
          </div>
          <div class="form-group">
            <label for="street">Улица</label>
            <input type="text" id="street" v-model="formReg.street">
          </div>
          <div class="form-group">
            <label for="house">Дом</label>
            <input type="text" id="house" v-model="formReg.house">
          </div>
        </div>
        <!-- Паспорт -->
        <div>
          <div class="form-group">
            <label for="documentType">Тип документа<span>*</span></label>
            <select id="documentType" @blur="$v.formReg.documentType.$touch()" v-model="formReg.documentType" >
              <option value="passport">Паспорт</option>
              <option value="birthCertificate">Свидетельство о рождении</option>
              <option value="driverLicense">Водительское удостоверение</option>
            </select>
            <div v-if="$v.formReg.documentType.$dirty">
              <div v-if="!$v.formReg.documentType.required" class="invalid">Поле обязательно для заполнения</div>
              <div v-if="!$v.formReg.documentType.alpha" class="invalid">В поле не должно содержаться цифры<br> и другие символы</div>
            </div>
          </div>
          <div class="form-group">
            <label for="passportSeries">Серия</label>
            <input type="text" id="passportSeries" v-model="formReg.passportSeries">
          </div>
          <div class="form-group">
            <label for="passportNumber">Номер</label>
            <input type="text" id="passportNumber" v-model="formReg.passportNumber">
          </div>
          <div class="form-group">
            <label for="passportIssuedBy">Кем выдан</label>
            <input type="text" id="passportIssuedBy" v-model="formReg.passportIssuedBy">
          </div>
          <div class="form-group">
            <label for="passportIssueDate">Дата выдачи<span>*</span></label>
            <input type="date" @blur="$v.formReg.passportIssueDate.$touch()" id="passportIssueDate" v-model="formReg.passportIssueDate" >
            <div v-if="$v.formReg.passportIssueDate.$dirty">
              <div v-if="!$v.formReg.passportIssueDate.required" class="invalid">Поле обязательно для заполнения</div>
            </div>
          </div>
          <div class="form-group btn">
            <button type="submit" class="submit-button" :disabled="disabledButton"  @click="submitForm()">Создать</button>
          </div>
        </div>     
      </div>

    </form>
    
  </div>
</template>

<script>
import { required, helpers, numeric, maxLength, minLength, } from 'vuelidate/lib/validators'
const alpha = helpers.regex('alpha', /^[a-zA-Za-яёА-ЯЁ]*$/)
const startsWithSeven = value => /^7/.test(value)

export default {
  data() {
    return {
      formReg: {
        // Атрибуты формы
        surname: '',
        name: '',
        patronymic: '',
        dob: '',
        phone: '',
        gender: '',
        customerGroup: [],
        doctor: '',
        noSMS: false,

        // Адрес
        zip: '',
        country: '',
        region: '',
        city: '',
        street: '',
        house: '',

        // Паспорт
        documentType: '',
        passportSeries: '',
        passportNumber: '',
        passportIssuedBy: '',
        passportIssueDate: ''
      },
    
    };
  },

  validations: {
    formReg: {
      surname: { required, alpha },
      name: { required, alpha },
      dob: { required },
      phone: { required, numeric, minLength: minLength(11), maxLength:maxLength(11),  startsWithSeven },
      customerGroup: { required },
      city: { required, alpha },
      documentType: { required, alpha },
      passportIssueDate: { required }
    }
  },

  computed: {
    disabledButton() {
      return this.$v.formReg.surname.$invalid ||
            this.$v.formReg.name.$invalid ||
            this.$v.formReg.dob.$invalid ||
            this.$v.formReg.phone.$invalid ||
            this.$v.formReg.customerGroup.$invalid ||
            this.$v.formReg.city.$invalid ||
            this.$v.formReg.documentType.$invalid ||
            this.$v.formReg.passportIssueDate.$invalid 
    }
  },
  methods: {
    submitForm() {
      this.$v.$touch();
      if (!this.$v.$invalid) {    
        alert('Новый клиент успешно создан!');
      }
    }
  }
  
};
</script>

<style>
.form-container {
  text-align: center;
  font-size: 16px;
  margin: 50px;
  margin-top: 20px;
}

.forms {
  display: flex;
  justify-content: space-around;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #f9f9f9;
  width: 100%;
  text-align: left;
}

.form-group {
  margin-bottom: 20px;
}
.invalid {
  font-size: 14px;
  width: 100%;
  color: red;
  
}

.form-group label {
  font-weight: bold;
}

.form-group span {
  color: red;
  margin-left: 5px;
  font-size: 14px;
}

input[type="text"],
input[type="tel"],
input[type="date"],
select {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.btn {
  text-align: center;
}
.submit-button {
  margin-top: 300px;
  padding: 10px 100px;
  color: #fff;
  background-color: #197a28;
  border: 1px solid #197a28;
  border-radius: 4px;
  font-size: 18px;
  cursor: pointer;
  transition: 0.25s linear;
}

.submit-button:hover {
  background-color: white;
  color: #197a28;
  border: 1px solid #197a28;
}


</style>
