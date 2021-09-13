<template>
  <div class="s1 s">01</div>
  <div class="content">
    <div class="texts">
      <p class="FPPB">
        Фабрика по производству биороботов
      </p>
      <p class="KMK">
        класса «монитор-кресло»
      </p>
    </div>
    <div class="imgs">
      <img src="../img/Subtract.png" class="subtract" />
      <img src="img/Subtract_2.png" class="subtract2" />
      <div class="Ellipse4"></div>
    </div>
  </div>

  <div class="sv">
    <div class="skroll">скролл</div>
    <div class="vector"></div>
  </div>

  <div class="s2 s">02</div>

  <div>
    <p class="keyMon">Кошелёк криптовалют</p>
    <div class="coins">
      <div class="coin" id="input0">
        <img :src="img" v-for="(i, index) in gold" :key="index" alt="coin" />
      </div>
    </div>

    <p class="mon">{{ gold }} biorobo монет</p>

    <button class="puy" id="goldAdd" @click="addGold">Нацыганить</button>

    <input
      class="custom-checkbox"
      id="checkbox"
      type="checkbox"
      v-model="checked"
    />
    <label for="checkbox" class="BuyCoin">Цыганить по 5 монет</label>
  </div>

  <div class="s3 s">03</div>

  <div class="cards">
    <p class="Shops">Рынок комплектующих</p>
    <div class="items">
      <div class="card" v-for="(item, index) in shop" :key="index">
        <div class="ico">
          <div class="red"></div>
          <img :src="item.img" />
        </div>
        <p class="bio">{{ item.title }}</p>
        <p class="pay">Стоимость: {{ item.price }} монет</p>
        <button class="made" v-on:click="buy(index)">Установить</button>
      </div>
    </div>
  </div>

  <div class="s4 s">04</div>
  <div>
    <p class="stock">Склад</p>
    <div class="stocks items">
      <div class="cardB shop-item" v-for="(item, index) in items" :key="index">
        <p class="bio">{{ shop[item.index].title }}</p>
        <p class="pay">Стоимость: {{ shop[item.index].sold }} монет</p>
        <p class="Amount">{{ item.count }} шт</p>
        <button class="madeS" @click="sold(index)">Продать</button>
      </div>
    </div>
  </div>

  <div class="s5 s"><a name="make"></a>05</div>

  <div>
    <p class="Production">Производство</p>
    <div class="radio">
      <p class="TypeStab">Тип биоробота:</p>
      <form action="">
        <div class="width">
          <label class="custom-radio">
            <input
              type="radio"
              name="Type"
              value="FrontEnd"
              v-model="pickedType"
            />
            <span>FrontEnd</span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="Type"
              value="Design"
              v-model="pickedType"
            />
            <span>Design</span>
          </label>
        </div>
      </form>
      <div class="radios">
        <p class="TypeStab">Стабилизатор:</p>
        <div class="width">
          <label class="custom-radio">
            <input
              type="radio"
              name="gender"
              value="Male"
              v-model="pickedgender"
            />
            <span>Male</span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="gender"
              value="Female"
              v-model="pickedgender"
            />
            <span>Female</span>
          </label>
        </div>
      </div>
    </div>
    <div class="alone"><img :src="Robot" /></div>
    <div class="buttons">
      <div class="checkboxs">
        <input
          class="Iconmeh-checkbox"
          type="checkbox"
          id="color-1"
          name="color-1"
        />
        <label for="color-1"></label>
      </div>
      <div class="checkboxs">
        <input
          class="Iconmeh-checkbox"
          type="checkbox"
          id="color-2"
          name="color-2"
        />
        <label for="color-2"></label>
      </div>
      <div class="checkboxs">
        <input
          class="Iconmeh-checkbox"
          type="checkbox"
          id="color-3"
          name="color-3"
        />
        <label for="color-3"></label>
      </div>
      <div class="checkboxs">
        <input
          class="Iconmeh-checkbox"
          type="checkbox"
          id="color-4"
          name="color-4"
        />
        <label for="color-4"></label>
      </div>
      <div class="checkboxs">
        <input
          class="hear-checkbox"
          type="checkbox"
          id="hear-1"
          name="hear-1"
        />
        <label for="hear-1"></label>
      </div>
      <div class="checkboxs">
        <input
          class="hear-checkbox"
          type="checkbox"
          id="hear-2"
          name="hear-2"
          value="red"
        />
        <label for="hear-2"></label>
      </div>
      <div class="checkboxs">
        <input
          class="hear-checkbox"
          type="checkbox"
          id="hear-3"
          name="hear-3"
        />
        <label for="hear-3"></label>
      </div>
      <div class="checkboxs">
        <input
          class="hear-checkbox"
          type="checkbox"
          id="hear-4"
          name="hear-4"
          value="yellow"
        />
        <label for="hear-4"></label>
      </div>
      <div class="checkboxs">
        <input
          class="ghost-checkbox"
          type="checkbox"
          id="ghost1"
          name="ghost1"
          value="yellow"
        />
        <label for="ghost1"></label>
      </div>
    </div>
    <button class="makesd" :active="isHasMoneyAndAllDetails">
      Произвести за 10 монет
    </button>
    <p class="textbuy" v-for="(item, index) in items" :key="index">
      <!-- Для производства биоробота не хватает, -->
      {{item1}}биомеханизма,
      {{item2}}процессора и{{item3}}души
    </p>
  </div>
  <div id="openModal" class="modal">
    <div class="modal-bg"></div>
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <div class="ImgCoin"></div>
          <h3 class="modal-title">Количество монет ограничено</h3>
          <div id="close">
            <div class="Rectangle20"></div>
            <div class="Rectangle21"></div>
          </div>
        </div>
        <div class="modal-body">
          <p>Вы не можете нацыганить более 100 монет biorobo</p>
        </div>
      </div>
    </div>
  </div>
  <div id="NotModal" class="modal">
    <div class="modal-bg"></div>
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <div class="NotCoin"></div>
          <h3 class="modal-title">Время циганить голду</h3>
          <div id="closer" class="clse">
            <div class="Rectangle20"></div>
            <div class="Rectangle21"></div>
          </div>
        </div>
        <div class="modal-body">
          <p>У вас нету голды biorobo, самое время циганить!</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Base',
  data () {
    return {
    //   substracFirst: require('../img/Subtract.png')
    }
  }
}
</script>
