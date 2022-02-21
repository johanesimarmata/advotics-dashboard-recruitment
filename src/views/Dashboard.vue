<template>
     <v-container fluid style="padding:40px;">
          <v-row class="d-flex flex-column flex-sm-column flex-md-row justify-space-between align-center">
               <h2 class="pageTitle">Dashboard</h2>
               <calendar-modal/>
          </v-row>
          <v-row justify="space-between" class="marketInsightsComponent">
               <h3>MARKET INSIGHTS</h3>
               <v-btn text class="helpComponent text--white" style="text-transform: none;">
                    <v-img
                         src="../assets/images/Help.png"
                         max-width="20"
                         max-height="20"
                         style="margin: 0px 4px;"
                    >
                    </v-img>
                    <p class="clickForHelp">Click Here for Help</p>
                    <v-icon class="chevronUp" style="color:white;">mdi-chevron-up</v-icon>
               </v-btn>
          </v-row>
          <v-row style="margin-top: 16px" justify="center" justify-sm="start">
               <v-card
                    max-width="300"
                    outlined
               >
                    <v-list-item three-line>
                         <v-list-item-content>
                              <div class="mb-4 cardTitleComponent">
                                   <h4>Sales Turnover</h4>
                                   <v-btn
                                        color="black"
                                        icon
                                   >
                                        <v-icon>mdi-dots-vertical</v-icon>
                                   </v-btn>
                              </div>
                              <div class="cardContent">
                                   <div class="cardContentText">
                                        <h4>Rp 3,600,000</h4>
                                        <p><span style="color: red; font-weight: 600"><v-icon style="color:red;">mdi-arrow-down-bold</v-icon> 13.8%</span> last period in products sold</p>
                                   </div>
                                   <v-img
                                        src="../assets/images/Sales Turnover.png"
                                        width="45"
                                        height="45"
                                        max-height="45"
                                        max-width="45"
                                   >

                                   </v-img>
                              </div>
                         </v-list-item-content>
                    </v-list-item>
               </v-card>
          </v-row>
          <v-row style="margin-top: 20px" class="d-flex">
               <v-col
                    xs="12"
                    sm="12"
                    md="7"
                    lg="5"
                    xl="5"
                    style="background-color: #ffffff;"
               >
                    <v-row justify="space-between" class="averagePurchaseValueComponent" style="color:#4D4F5C; padding: 15px;">
                         <h6 style="font-size:20px;">AVERAGE PURCHASE VALUE</h6>
                         <v-col md="6" class="d-flex justify-end align-center">
                              <v-select
                                   :items="items"
                                   label="Duration"
                                   v-model="selectedDuration"
                                   solo
                              ></v-select>
                              <v-spacer/>
                              <v-btn
                                   color="black"
                                   icon
                              >
                                   <v-icon>mdi-dots-vertical</v-icon>
                              </v-btn>
                         </v-col>
                    </v-row>
                    <v-row>
                         <v-col>
                              <chart/>
                         </v-col>
                    </v-row>
               </v-col>
               <v-col xs="12" sm="12" md="4" lg="3" xl="3" class="bestSellingSKU" style="background-color:#ffffff;">
                    <v-row justify="space-between" align="center" style="padding:16px;">
                         <h6 style="font-size:20px;">BEST SELLING SKU</h6>
                         <v-btn
                              color="black"
                              icon
                         >
                              <v-icon>mdi-dots-vertical</v-icon>
                         </v-btn>
                    </v-row>
                    <product-card
                         v-for="product in bestSellingSKUProduct"
                         :key="`sku-`+ product.id"
                         :productData="product"
                         :selectedProduct="selectedSellingSKUProduct"
                         @click.native="changeProductSelling(product.id)"
                    />
               </v-col>
               <v-col xs="12" sm="12" md="4" lg="3" xl="3" class="topCompetitorSKU" style="background-color:#ffffff;">
                    <v-row justify="space-between" align="center" style="padding:16px;">
                         <h6 style="font-size:20px;">TOP COMPETITOR SKU</h6>
                         <v-btn
                              color="black"
                              icon
                         >
                              <v-icon>mdi-dots-vertical</v-icon>
                         </v-btn>
                    </v-row>
                    <product-card
                         v-for="product in topCompetitorSKUProduct"
                         :key="`sku-`+ product.id"
                         :productData="product"
                         :selectedProduct="selectedCompetitorSKUProduct"
                         @click.native="changeProductCompetitor(product.id)"                    
                    />
               </v-col>
          </v-row>
     </v-container>
</template>

<script>
import CalendarModal from '../components/CalendarModal.vue'
import ProductCard from '../components/ProductCard.vue'
import Chart from '../components/Chart.vue'
export default {
     name: 'Dashboard',
     components: {
          CalendarModal,
          ProductCard,
          Chart
     },
     data(){
          return{
               items: ['Last 6 Months', 'Last Month', 'Last Week', 'Yesterday'],
               selectedDuration: 'Last 6 Months',
               bestSellingSKUProduct: [
                    {id: 1, name: 'Danone', harga: 'Rp 10.000', jumlahTerjual: 1000},
                    {id: 2, name: 'Danone', harga: 'Rp 11.000', jumlahTerjual: 900},
                    {id: 3, name: 'Danone', harga: 'Rp 12.000', jumlahTerjual: 800},
                    {id: 4, name: 'Danone', harga: 'Rp 13.000', jumlahTerjual: 700},
                    {id: 5, name: 'Danone', harga: 'Rp 14.000', jumlahTerjual: 600}
               ],
               topCompetitorSKUProduct: [
                    {id: 1, name: 'Danone', harga: 'Rp 10.000', jumlahTerjual: 11000},
                    {id: 2, name: 'Danone', harga: 'Rp 11.000', jumlahTerjual: 10000},
                    {id: 3, name: 'Danone', harga: 'Rp 9.000', jumlahTerjual: 8000},
                    {id: 4, name: 'Danone', harga: 'Rp 15.000', jumlahTerjual: 7000},
                    {id: 5, name: 'Danone', harga: 'Rp 7.000', jumlahTerjual: 5000}
               ],
               selectedSellingSKUProduct: 1,
               selectedCompetitorSKUProduct: 1
          }
     },
     methods:{
          changeProductSelling(id){
               this.selectedSellingSKUProduct = id
          },
          changeProductCompetitor(id){
               this.selectedCompetitorSKUProduct = id
          }
     }
}
</script>

<style scoped>
     @import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap');
     *{
          font-family: 'Source Sans Pro', sans-serif;
     }
     h2.pageTitle{
          font-size: 40px;
          color: #707070;
          font-weight: 600;
     }

     .marketInsightsComponent{
          padding: 12px 16px;
          margin-top: 30px;
          border: 2px;
          background-color: #37B04C;
          color: #ffffff;
          font-size: 20px;
          display: flex;
          flex-direction: row;
          justify-content: space-between;
     }

     .marketInsightsComponent .helpComponent{
          display: flex;
          align-items: center;
     }

     .clickForHelp{
          font-size: 14px;
          text-decoration: underline;
          font-weight: 300;
          margin-bottom: 0px;
          margin-right: 16px;
          color: white;
     }

     .chevronUp{
          width: 15px;
          height: 9px;
          color: #ffffff;
     }

     .cardTitleComponent{
          width: 100%;
          display: flex;
          justify-content: space-between;
          color: #D2D2D2;
     }

     .cardTitleComponent h4{
          margin: auto 0;
          font-weight: 300;
          letter-spacing: 0.5px;
     }

     .cardContent{
          display: flex;
          justify-content: space-between;
     }
     
     .cardContentText{
          display: flex;
          flex-direction: column;
     }

     .cardContentText h4{
          font-size: 22px;
          font-weight: bold;
          text-align: left;
          margin-bottom: 7px;
     }

     .cardContentText p{
          font-size: 12px;
          font-weight: 300;
          color: #D2D2D2;
     }
     .v-input{
          max-width: 165px;
          display: flex;
          max-height: 50px;
     }

     .averagePurchaseValueComponent{
          display: flex;
          align-items: center;
     }

     .topCompetitorSKU{
          margin-left: 16px;
     }

     .bestSellingSKU{
          margin-left: 16px;
     }

     @media screen and (max-width: 1585px) and (min-width: 1264px){
          .averagePurchaseValueComponent{
               display: flex;
               flex-direction: column;
               align-items: center;
          }
     }

     @media screen and (max-width: 1263px){
          .topCompetitorSKU{
               margin-top: 15px;
               margin-left: 0px;
          }
     }

     @media screen and (max-width: 1171px) and (min-width: 960px){
          .averagePurchaseValueComponent{
               display: flex;
               flex-direction: column;
               align-items: center;
          }
     }

     @media screen and (max-width: 959px){
          .bestSellingSKU{
               margin-top: 15px;
               margin-left: 0;
          }
     }

     @media screen and (max-width: 677px) {
          .averagePurchaseValueComponent{
               display: flex;
               flex-direction: column;
               align-items: center;

          }
     }

     @media screen and (max-width: 599px) {
          .marketInsightsComponent{
               display: flex;
               flex-direction: column;
               align-items: center;
          }
     }
</style>