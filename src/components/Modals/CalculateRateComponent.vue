<template>
  <div class="modal-rate-wrapper">
    <div class="modal-rate">
      <h1 class="modal-rate__header">
        ЗАПОЛНИТЕ ФОРМУ ЗАЯВКИ, И МЫ РАССЧИТАЕМ СТОИМОСТЬ ГРУЗОПЕРЕВОЗКИ
      </h1>
      <form onsubmit="return false">
        <div class="modal-rate__first-column">
          <div class="company-name-wrapper">
            <input
              type="text"
              placeholder="Полное имя компании *"
              v-model="CompanyName"
              class="company-name"
              required
            />
            <img
              class="company-name-image"
              src="@/assets/icons/red-earth.svg"
              alt=""
            />
          </div>
          <div class="from-country-wrapper">
            <input
              type="text"
              placeholder="Откуда (страна)  *"
              v-model="FromCountry"
              class="from-country"
              required
            />
            <img
              class="from-country-img"
              src="@/assets/icons/white-arrow-left.svg"
              alt=""
            />
          </div>
          <div class="to-country-wrapper">
            <input
              type="text"
              placeholder="Куда (страна)  *"
              v-model="ToCountry"
              class="to-country"
              required
            />
            <img
              class="to-country-img"
              src="@/assets/icons/white-arrow-right.svg"
              alt=""
            />
          </div>
          <div class="station-from-wrapper">
            <input
              type="text"
              placeholder="Станция отправления *"
              v-model="StationFrom"
              class="station-from"
              required
            />
            <img
              class="station-from-img"
              src="@/assets/icons/red-location.svg"
              alt=""
            />
          </div>
          <div class="station-to-wrapper">
            <input
              type="text"
              placeholder="Станция назначения *"
              v-model="StationTo"
              class="station-to"
              required
            />
            <img
              class="station-to-img"
              src="@/assets/icons/red-location.svg"
              alt=""
            />
          </div>
        </div>
        <div class="modal-rate__second-column">
          <div class="your-name-wrapper">
            <input
              type="text"
              placeholder="Имя\Фамилия *"
              v-model="YourName"
              class="your-name"
              required
            />
            <img
              class="your-name-img"
              src="@/assets/icons/red-person.svg"
              alt=""
            />
          </div>
          <div class="luggage-info-wrapper">
            <input
              type="text"
              placeholder="ГНГ и ЕТСНГ груза *"
              v-model="LuggageInfo"
              class="luggage-info"
              required
            />
            <img
              class="luggage-info-img"
              src="@/assets/icons/red-box.svg"
              alt=""
            />
          </div>
          <div class="luggage-weight-wrapper">
            <input
              type="text"
              placeholder="Вес груза в вагоне *"
              v-model="LuggageWeight"
              class="Luggageweight"
              required
            />
            <img
              class="luggage-weight-img"
              src="@/assets/icons/red-scales.svg"
              alt=""
            />
          </div>
          <div class="train-type-wrapper">
            <input
              type="text"
              placeholder="Вид подвижного состава *"
              v-model="TrainType"
              class="train-type"
              required
            />
            <img
              class="train-type-img"
              src="@/assets/icons/red-train.svg"
              alt=""
            />
          </div>
          <div class="train-own-wrapper">
            <input
              type="text"
              placeholder="Принадлежность подвижного состава *"
              v-model="TrainOwn"
              class="train-own"
              required
            />
            <img
              class="train-own-img"
              src="@/assets/icons/red-search.svg"
              alt=""
            />
          </div>
        </div>
        <div class="modal-rate__third-column">
          <div class="your-phone-wrapper">
            <input
              type="tel"
              v-model="YourPhone"
              class="your-phone"
              placeholder="+7 (___) ___-__-__  *"
              required
            />
            <img
              class="your-phone-img"
              src="@/assets/icons/red-phone.svg"
              alt=""
            />
          </div>
          <div class="your-mail-wrapper">
            <input
              type="email"
              v-model="YourMail"
              class="your-mail"
              placeholder="E-mail *"
              required
            />
            <img
              class="your-mail-img"
              src="@/assets/icons/red-mail.svg"
              alt=""
            />
          </div>
          <div class="your-message-wrapper">
            <textarea
              name="rate-message"
              v-model="YourMessage"
              class="your-message"
              placeholder="Комментарий  *"
              required
            />
            <img
              class="your-message-img"
              src="@/assets/icons/red-chat.svg"
              alt=""
            />
          </div>
        </div>
        <div class="send-checkboxes">
          <button class="modal-rate-btn-send" @click="callSendRate()">
            Отправить
          </button>
          <div class="checkboxes-wrapper">
            <h4 class="checkboxes-title">Виды связи</h4>
            <div class="checkboxes">
              <input type="checkbox" />
              <img
                class="checkbox-phone"
                src="@/assets/icons/red-phone.svg"
                alt=""
              />
              <p>Телефон</p>
              <input type="checkbox" />
              <img
                class="checkbox-email"
                src="@/assets/icons/red-mail.svg"
                alt=""
              />
              <p>E-mail</p>
              <input type="checkbox" />
              <img
                class="checkbox-messanger"
                src="@/assets/icons/red-messanger.svg"
                alt=""
              />
              <p>Мессенджер</p>
            </div>
          </div>
        </div>
      </form>
      <button class="modal-rate-close" @click="closeRate()">&#10006;</button>
    </div>
    <RateSendComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import RateSendComponent from "@/components/Modals/RateSendComponent.vue";

@Component({
  components: {
    RateSendComponent,
  },
})
export default class CalculateRateComponent extends Vue {
  CompanyName = "";
  FromCountry = "";
  ToCountry = "";
  StationFrom = "";
  StationTo = "";
  YourName = "";
  LuggageInfo = "";
  LuggageWeight = "";
  TrainType = "";
  TrainOwn = "";
  YourPhone = "";
  YourMail = "";
  YourMessage = "";
  closeRate() {
    const closerate: HTMLElement = document.querySelector(
      ".modal-rate-wrapper"
    ) as HTMLElement;
    const bodyModalRate: HTMLElement = document.querySelector(
      "body"
    ) as HTMLElement;

    closerate.style.opacity = "0";
    closerate.style.visibility = "hidden";
    bodyModalRate.addEventListener("click", (event) => {
      if (event.target === closerate) {
        closerate.style.opacity = "0";
        closerate.style.visibility = "hidden";
      }
    });
  }
  callSendRate() {
    const callSendRateElement: HTMLElement = document.querySelector(
      ".modal-send-rate-wrapper"
    ) as HTMLElement;
    if (
      (this.CompanyName === "",
      this.FromCountry === "",
      this.ToCountry === "",
      this.StationFrom === "",
      this.StationTo === "",
      this.YourName === "",
      this.LuggageInfo === "",
      this.LuggageWeight === "",
      this.TrainType === "",
      this.TrainOwn === "",
      this.YourPhone === "",
      this.YourMail === "",
      this.YourMessage === "")
    ) {
      return;
    } else {
      callSendRateElement.style.opacity = "1";
      callSendRateElement.style.visibility = "visible";
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.modal-rate-wrapper {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  visibility: hidden;
  opacity: 0;
  transition: 0.5s;
  z-index: 1000;
  .modal-rate {
    min-width: toVw(1303px);
    min-height: toVw(658px);
    position: relative;
    background-color: #ffffff;
    margin: auto;
    border-radius: toVw(22px);
    padding: toVw(57px) toVw(95px) toVw(67px) toVw(100px);
    .modal-rate__header {
      width: toVw(950px);
      font-size: toVw(32px);
      font-weight: 800;
      color: #172675;
      margin-bottom: toVw(35px);
    }
    form {
      display: flex;
      flex-direction: row;
      gap: toVw(17px);
      input {
        padding: toVw(21px) toVw(20px) toVw(20px) toVw(48px);
        border: toVw(1px) solid #8e8e8e;
        border-radius: toVw(8px);
        font-size: toVw(14px);
        font-weight: 500;
        color: #535353;
        &::placeholder {
          font-size: toVw(14px);
          font-weight: 500;
          color: #535353;
        }
      }
      textarea {
        padding: toVw(20px) toVw(52px);
        border: toVw(1px) solid #8e8e8e;
        border-radius: toVw(8px);
        max-width: toVw(358px);
        min-height: toVw(204px);
        font-size: toVw(14px);
        font-weight: 500;
        color: #535353;
        &::placeholder {
          font-size: toVw(14px);
          font-weight: 500;
          color: #535353;
        }
      }
      .modal-rate__first-column {
        input {
          min-width: toVw(358px);
        }
        display: flex;
        gap: toVw(15px);
        flex-direction: column;
        .company-name-wrapper {
          position: relative;
          .company-name-image {
            position: absolute;
            width: toVw(16px);
            height: toVw(16px);
            top: toVw(20px);
            left: toVw(17px);
          }
        }
        .from-country-wrapper {
          position: relative;
          .from-country-img {
            background-color: #ff1515;
            position: absolute;
            border-radius: 50%;
            padding: toVw(6px);
            top: toVw(20px);
            left: toVw(17px);
          }
        }
        .to-country-wrapper {
          position: relative;
          .to-country-img {
            background-color: #ff1515;
            position: absolute;
            border-radius: 50%;
            padding: toVw(6px);
            top: toVw(20px);
            left: toVw(17px);
          }
        }
        .station-from-wrapper {
          position: relative;
          .station-from-img {
            position: absolute;
            width: toVw(14px);
            height: toVw(18px);
            top: toVw(18px);
            left: toVw(18px);
          }
        }
        .station-to-wrapper {
          position: relative;
          .station-to-img {
            position: absolute;
            width: toVw(14px);
            height: toVw(18px);
            top: toVw(18px);
            left: toVw(18px);
          }
        }
      }
      .modal-rate__second-column {
        input {
          min-width: toVw(358px);
        }
        .your-name-wrapper {
          position: relative;
          .your-name-img {
            position: absolute;
            width: toVw(15px);
            height: toVw(15px);
            top: toVw(21px);
            left: toVw(21px);
          }
        }
        .luggage-info-wrapper {
          position: relative;
          .luggage-info-img {
            position: absolute;
            width: toVw(16px);
            height: toVw(16px);
            top: toVw(21px);
            left: toVw(21px);
          }
        }
        .luggage-weight-wrapper {
          position: relative;
          .luggage-weight-img {
            position: absolute;
            width: toVw(21px);
            height: toVw(16px);
            top: toVw(19px);
            left: toVw(19px);
          }
        }
        .train-type-wrapper {
          position: relative;
          .train-type-img {
            position: absolute;
            width: toVw(25px);
            height: toVw(25px);
            top: toVw(17px);
            left: toVw(21px);
          }
        }
        .train-own-wrapper {
          position: relative;
          .train-own-img {
            position: absolute;
            width: toVw(16px);
            height: toVw(16px);
            top: toVw(20px);
            left: toVw(23px);
          }
        }
        display: flex;
        gap: toVw(15px);
        flex-direction: column;
        input {
          max-width: toVw(358px);
          padding-left: toVw(56px);
        }
      }
      .modal-rate__third-column {
        input {
          min-width: toVw(358px);
          padding-left: toVw(52px);
        }
        textarea {
          min-width: toVw(358px);
        }
        display: flex;
        gap: toVw(15px);
        flex-direction: column;
        .your-phone-wrapper {
          position: relative;
          .your-phone-img {
            position: absolute;
            width: toVw(20px);
            height: toVw(20px);
            top: toVw(20px);
            left: toVw(20px);
          }
        }
        .your-mail-wrapper {
          position: relative;
          .your-mail-img {
            position: absolute;
            width: toVw(17px);
            height: toVw(12px);
            top: toVw(23px);
            left: toVw(20px);
          }
        }
        .your-message-wrapper {
          position: relative;
          .your-message-img {
            position: absolute;
            width: toVw(15px);
            height: toVw(15px);
            top: toVw(20px);
            left: toVw(20px);
          }
        }
      }
    }
    .send-checkboxes {
      position: absolute;
      bottom: toVw(57px);
      left: toVw(100px);
      display: flex;
      justify-content: space-between;
      align-items: center;
      .modal-rate-btn-send {
        font-size: toVw(15px);
        font-weight: 500;
        background-color: #ff1515;
        padding: toVw(16px) toVw(32px);
        border-radius: toVw(7px);
        border: none;
        color: #ffffff;
        margin-right: toVw(33px);
        cursor: pointer;
      }
      .checkboxes-wrapper {
        display: flex;
        .checkboxes-title {
          margin-right: toVw(30px);
          font-size: toVw(15px);
          font-weight: 700;
          color: #8e8e8e;
        }
        .checkboxes {
          display: flex;
          align-items: center;
          input {
            border: none;
            margin-right: toVw(11px);
          }
          img {
            margin-right: toVw(6px);
          }
          .checkbox-phone {
            width: toVw(20px);
            height: toVw(20px);
          }
          .checkbox-email {
            width: toVw(17px);
            height: toVw(12px);
          }
          .checkbox-messanger {
            width: toVw(20px);
            height: toVw(19px);
          }
          p {
            margin-right: toVw(35px);
            font-size: toVw(14px);
            font-weight: 500;
            color: #8e8e8e;
          }
        }
      }
    }
  }
  .modal-rate-close {
    position: absolute;
    top: toVw(42px);
    right: toVw(34px);
    color: red;
    font-size: toVw(25px);
    z-index: 100;
    cursor: pointer;
    border: none;
    background: none;
  }
}
</style>
