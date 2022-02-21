<template>
     <v-row class="d-flex flex-row">
          <v-col class="d-flex justify-center">
               <v-card
                    outlined
                    max-width="300"
                    width="300"
                    v-bind:class="selectedProduct === productData.id ? 'selected' : ''"
               >
                    <v-list-item three-line style="padding:0;">
                         <v-list-item-content style="padding:0;">
                              <div class="productContent">
                                   <v-img
                                        src="../assets/images/Product.png"
                                        max-width="80"
                                        max-height="88"
                                        height="88"
                                   >
                                   </v-img>
                                   <div class="productText">
                                        <h4 style="color: rgba(0, 0, 0, 222); font-weight: 400;"
                                             v-bind:style="selectedProduct === productData.id ? 'font-size: 22px; ' : 'font-size: 18px;'"
                                        >{{productData.name}}</h4>
                                        <div class="hargaJumlahComponent" v-bind:style="selectedProduct === productData.id ? 'font-size: 16px; ' : 'font-size: 14px;'">
                                             <p>{{productData.harga}}</p>
                                             <v-spacer></v-spacer>
                                             <p>{{productData.jumlahTerjual}}</p>
                                        </div>
                                   </div>
                              
                              </div>
                         </v-list-item-content>
                    </v-list-item>
               </v-card>
          </v-col>
     </v-row>
</template>

<script>
export default {
     name: 'ProductCard',
     props: ['productData', 'selectedProduct']
}
</script>

<style scoped>
     @import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');

     *{
         font-family: 'Open Sans', sans-serif;
     }

     p{
          margin-bottom: 0;
     }
     
     .selected{
          background-color: #FFE7BD;
     }


     .productContent{
          display: flex;
          justify-content: flex-start;
          width: 100%;
     }

     .productText{
          text-align: left;
          margin-left: 10px;
          display: flex;
          flex-direction: column;
          justify-content: center;
          width: 60%;
          padding: 10px;
          color: #00000099;
          font-size: 14px;
     }

     .hargaJumlahComponent{
          display: flex;
          flex-direction: row;
     }
</style>