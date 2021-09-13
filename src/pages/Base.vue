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
      <img :src="getImgUrl(substracFirst)" class="subtract" />
      <img :src="getImgUrl(substracSecond)" class="subtract2" />
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
        <img :src="getImgUrl(imgCoin)" v-for="(i, index) in gold" :key="index" alt="coin" />
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
      substracFirst: 'Subtract',
      substracSecond: 'Subtract_2',
      imgCoin: 'coin',
      checked: false,
      isHasMoneyAndAllDetails: true,
      gold: 99,
      shop: [{
        title: 'Биомеханизм',
        price: 7,
        sold: 5,
        img: './img/Subtract3.png'
      },
      {
        title: 'Процессор',
        price: 5,
        sold: 3,
        img: './img/Vector2.png'
      },
      {
        title: 'Душа',
        price: 25,
        sold: 15,
        img: './img/Soul .png'
      }
      ],
      item2: 4,
      item3: 1,
      items: [],
      pickedType: 'FrontEnd',
      pickedgender: 'Male'
    }
  },
  methods: {
    getImgUrl (image) {
      return `/img/${image}.png`
    },
    addGold: function () {
      if (this.gold >= 100) {
        // openModal.style.display = 'block'
        return
      }
      this.gold += this.checked ? 5 : 1
    },
    buy: function (index) {
      const item = this.shop[index]
      if (item.price > this.gold) {
        // NotModal.style.display = 'block'
        return
      }
      const i = this.items.findIndex(obj => obj.index === index)
      if (i >= 0) {
        this.items[i].count += 1
      } else {
        this.items.push({
          count: 1,
          index: index
        })
      }
      this.gold -= item.price
    },
    sold: function (index) {
      const item = this.items[index]
      if (item.count <= 0) {
        return
      }
      const shopItem = this.shop[item.index]
      this.gold += shopItem.sold
      item.count -= 1
    }
  },
  mounted () {
    for (let i = 0; i < this.shop.length; i++) {
      this.items.push({ index: i, count: 0 })
    }
  },
  computed: {
    Robot () {
      if ((this.pickedType === 'FrontEnd') && (this.pickedgender === 'Female')) {
        return './img/nofrontFemale.png'
      } else if ((this.pickedType === 'FrontEnd') && (this.pickedgender === 'Male')) {
        return './img/nofrontMale.png'
      } else if ((this.pickedType === 'Design') && (this.pickedgender === 'Female')) {
        return './img/noDesignerFemale.png'
      } else {
        return './img/noDesignerMale.png'
      }
    },
    item1 () {
      return 1
    }
  }
}
// document.addEventListener('DOMContentLoaded', function () {
//   var scrollbar = document.body.clientWidth - window.innerWidth + 'px'
//   document.querySelector('[href="#openModal"]').addEventListener('click', function () {
//     document.body.style.overflow = 'hidden'
//     document.querySelector('#openModal').style.marginLeft = scrollbar
//   })
//   document.querySelector('[href="#close"]').addEventListener('click', function () {
//     document.body.style.overflow = 'visible'
//     document.querySelector('#openModal').style.marginLeft = '0px'
//   })
// })
// document.getElementById('close').onclick = function () {
//   document.getElementById('openModal').style.display = 'none'
// }
// document.getElementById('closer').onclick = function () {
//   document.getElementById('NotModal').style.display = 'none'
// }
</script>
