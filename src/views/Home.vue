<template>
  <div class="home">
    <v-container>
      <v-row class="text-center">
        <v-col v-for="index in goodsList" :key="index" cols="12" md="4">
          <stock
            :image="index.img"
            :title="index.title"
            :price="index.price"
            @orderBuy="cBuy"
            @orderCancel="cCancel"
          />
        </v-col>
        <v-col>
          <v-dialog v-model="dialog" persistent max-width="400px">
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                color="green"
                style="margin-bottom: 30px"
                dark
                v-bind="attrs"
                v-on="on"
              >
                <span class="mr-2">basket</span>
                <v-icon>mdi-cart-outline</v-icon>
              </v-btn>
            </template>
            <v-card>
              <v-card-title>
                <span class="headline">Order List</span>
              </v-card-title>
              <v-card-text>
                <v-simple-table>
                  <template v-slot:default>
                    <thead>
                      <tr>
                        <th class="text-left">Name</th>
                        <th class="text-left">Price</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr v-for="i in orderSelect" :key="i">
                        <td class="text-left">{{ i.nameProduct }}</td>
                        <td class="text-left">{{ i.priceProduct }} ฿</td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
                <br />

                <h2 class="text-end">Total = {{ allPrice }}</h2>
              </v-card-text>

              <v-card-actions>
                <v-col
                  ><v-btn color="red darken-1" dark @click="dialog = false">
                    Exit
                  </v-btn></v-col
                >
                <v-spacer />
                <v-col
                  ><v-btn color="green darken-1" dark @click.once="calClick">
                    Calculate
                  </v-btn></v-col
                >
              </v-card-actions>
            </v-card>
          </v-dialog>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import stock from "@/components/Stock.vue";
export default {
  name: "Home",
  components: {
    stock
  },
  props: {
    nameProduct: String,
    priceProduct: Number,
    numberProduct: Number
  },
  data: () => ({
    goodsList: [
      {
        img:
          "https://www.battlefieldbeers.co.uk/clear_cf/pub-media-catalog-product-c-o-coke_can_2000x0.jpg",
        title: "Coke",
        price: 18
      },
      {
        img: "https://cf.shopee.co.th/file/68075f364cf7f0647536dda30a1fdaaf",
        title: "Pepsi",
        price: 15
      },
      {
        img: "https://images.heb.com/is/image/HEBGrocery/000561259",
        title: "Monster",
        price: 40
      },
      {
        img:
          "https://5.imimg.com/data5/UE/NE/WQ/SELLER-82456434/sprinte-cold-derink-500x500.jpg",
        title: "Sprint",
        price: 17
      },
      {
        img: "https://cf.shopee.co.th/file/8559d8a545248e0a7b85fad836c62150",
        title: "C-vitt",
        price: 16
      },
      {
        img:
          "https://backend.tops.co.th/media/catalog/product/8/8/8850228002025_e21-07-2020.jpg",
        title: "Mansome",
        price: 20
      },
      {
        img:
          "https://secure.ap-tescoassets.com/assets/TH/432/8851717907432/ShotType1_540x540.jpg",
        title: "Dutch Mill Hight Protien",
        price: 42
      },
      {
        img:
          "https://gda.thai-tba.or.th/wp-content/uploads/2018/07/mm-mandarin-pet-335-ml-th-new.png",
        title: "Minute Maid",
        price: 21
      },
      {
        img:
          "https://secure.ap-tescoassets.com/assets/TH/669/8854698009669/ShotType1_540x540.jpg",
        title: "Oishi Green Tea",
        price: 22
      }
    ],
    allPrice: 0,
    dialog: false,
    orderSelect: [],
    arrayPrice: []
  }),
  methods: {
    cBuy(value) {
      this.orderSelect.push(value);
      this.arrayPrice.push(value.priceProduct);
    },
    cCancel(value) {
      this.orderSelect.pop(value);
      this.arrayPrice.pop(value.priceProduct);
    },
    calClick() {
      for (var i = 0; i < this.arrayPrice.length; i++) {
        this.allPrice += this.arrayPrice[i];
      }
      alert("หากต้องการเพิ่มสินค้ากรุณากดปุ่มรีเฟรช!!");
    }
  }
};
</script>
