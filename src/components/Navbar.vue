<template>
          <v-card
               app
               class="mx-auto"
               width="100%"
               style="box-shadow: 0px 3px 6px #00000029"
          >
               <v-toolbar>
                    <v-toolbar-title class="grey--text toolbarLogo">
                         <v-img
                              src="https://www.advotics.com/wp-content/uploads/2019/07/advotics-logo-optimize.jpg"
                              max-height="45"
                              max-width="180"
                         >
                         </v-img>
                    </v-toolbar-title>
                    <v-spacer class="spacerNavbar"></v-spacer>
                    <v-toolbar-items class="toolbarItems">
                         <div class="infoProfile">
                              <p class="namaAkun">Username</p>
                              <p class="namaPerusahaan">Company Name</p>
                         </div>
                         <div class="buttonProfile">
                              <v-btn icon>
                                   <v-icon>mdi-account-circle</v-icon>
                              </v-btn>
                              <v-btn icon>
                                   <v-icon>mdi-logout-variant</v-icon>
                              </v-btn>
                         </div>
                    </v-toolbar-items>
               </v-toolbar>
               <v-divider></v-divider>
          </v-card>
</template>

<script>
export default {
     name: 'Navbar'
}
</script>

<style scoped>
     @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&family=Roboto:wght@400;500&display=swap');
     
     *{
          
     }
     p.namaAkun {
          font-size: 16px;
          color: #727272;
          font-weight: 600;
          margin: 0;
     }
     p.namaPerusahaan{
          font-size: 12px;
          color: #727272;
          font-weight: 300;
          margin: 0;

     }

     .infoProfile, .buttonProfile{
          margin: auto 0;
     }

     @media screen and (max-width: 599px) {
          .toolbarLogo{
               display: none;
          }
          .spacerNavbar{
               display: none;
          }
          .toolbarItems{
               width: 100%;
               display: flex;
               justify-content: space-between;
          }
     }
</style>