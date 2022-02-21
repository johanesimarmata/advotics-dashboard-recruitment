<template>
     <div class="text-center">
          <v-dialog
               v-model="dialog"
               width="800"
          >
               <template v-slot:activator="{ on, attrs }">
                    <v-btn
                         color="black"
                         v-bind="attrs"
                         v-on="on"
                         class="no-text-transform buttonPeriod"
                         block
                         outlined
                    >
                         <v-icon left>
                         mdi-calendar-month-outline
                         </v-icon>
                         <div class="periodWrap d-flex flex-column flex-sm-row justify-center align-center">
                              <p class="text-wrap" style="margin-bottom:0;">Period </p>
                              <p class="text-wrap" style="margin-bottom:0; margin-left: 10px;"> {{dateText}}</p>
                         </div>
                         <v-icon right>
                         mdi-chevron-down
                         </v-icon>
                    </v-btn>
               </template>

               <v-card>
                    <v-card-title class="text-h6 white lighten-2">
                         <v-icon left>mdi-calendar-month-outline</v-icon>
                         Period
                         <v-spacer></v-spacer>
                         <v-btn icon @click="dialog = false"><v-icon>mdi-close</v-icon></v-btn>
                    </v-card-title>

               <v-card-text>
                    <v-row justify="space-around" no-gutters>
                         <v-col :cols="3" class="d-flex flex-column justify-start">
                              <v-btn @click.stop="getToday" text style="text-align:left;">Today</v-btn>
                              <v-divider></v-divider>
                              <v-btn @click.stop="getYesterday" text style="text-align:left;">Yesterday</v-btn>
                              <v-divider></v-divider>
                              <v-btn @click.stop="getLast7Days" text style="text-align:left;">Last 7 days</v-btn>
                              <v-divider></v-divider>
                              <v-btn @click.stop="getLast30Days" text style="text-align:left;">Last 30 days</v-btn>
                              <v-divider></v-divider>
                              <v-btn @click.stop="getThisMonth" text style="text-align:left;">This Month</v-btn>
                              <v-divider></v-divider>
                              <v-btn text style="text-align:left;">Custom</v-btn>
                              <v-spacer></v-spacer>
                              <v-btn @click.stop="apply" color="success">Apply</v-btn>
                         </v-col>
                         <v-col :cols="9" class="d-flex flex-column flex-sm-column flex-md-row">
                              <v-date-picker
                                   no-title
                                   v-model="dateStart"
                                   :max="maxDate"
                                   color="green lighten-1"
                              ></v-date-picker>
                              <v-date-picker
                                   no-title
                                   v-model="dateEnd"
                                   color="green lighten-1"
                                   header-color="primary"
                                   :max="maxDate"
                              ></v-date-picker>
                         </v-col>
                    </v-row>
               </v-card-text>
               </v-card>
          </v-dialog>
     </div>
</template>

<script>
export default {
     name: 'CalendarModal',
     data () {
          return {
               dialog: false,
               dateText: '',
               maxDate: this.getDateByDay(1),
               statusPeriod: '',
               dateStart: (new Date((Date.now() - 7 * 86400000) - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
               dateEnd: (new Date((Date.now() - 86400000) - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)
          }
    },
    methods: {
         getDateByDay(numDay){
              return (new Date((Date.now() - numDay * 86400000) - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)
         },
         getToday(){
              this.dateStart = this.getDateByDay(0)
              this.dateEnd = this.getDateByDay(0)
              this.statusPeriod = 'today'
         },
         getYesterday(){
              this.dateStart = this.getDateByDay(1)
              this.dateEnd = this.getDateByDay(1)
              this.statusPeriod = 'yesterday'
         },
         getLast7Days(){
              this.dateStart = this.getDateByDay(7)
              this.dateEnd = this.getDateByDay(1)
              this.statusPeriod = 'last7days'
         },
         getLast30Days(){
              this.dateStart = this.getDateByDay(30)
              this.dateEnd = this.getDateByDay(1)
              this.statusPeriod = 'last30days'
         },
         getThisMonth(){
              let currentDate = this.getDateByDay(0)
              let currentDateSplit = currentDate.split('-')
              this.dateEnd = currentDate
              if(parseInt(currentDate[2]) > 1){
                   this.dateStart = this.getDateByDay(parseInt(currentDateSplit[2]) - 1)
              } else {
                   this.dateStart = currentDate
              }
              this.statusPeriod = 'thismonth'
         },
         getDatetext(){
              this.dateText =  `${this.dateStart}`
              if(this.dateStart === this.dateEnd){
                   this.dateText =  `${this.parseDate(this.dateStart)}`
              } else {
                   this.dateText = `${this.parseDate(this.dateStart)} - ${this.parseDate(this.dateEnd)}`
              }
         },
         parseDate(date){
              let dateArray = date.split('-')
              var month;
              switch(dateArray[1]){
                    case '01': 
                         month = 'January'
                         break
                    case '02':
                         month = 'February'
                         break
                    case '03':
                         month = 'March'
                         break
                    case '04':
                         month = 'April'
                         break
                    case '05':
                         month = 'May'
                         break
                    case '06':
                         month = 'June'
                         break
                    case '07': 
                         month = 'July'
                         break
                    case '08':
                         month = 'August'
                         break
                    case '09':
                         month = 'September'
                         break
                    case '10':
                         month = 'October'
                         break
                    case '11':
                         month = 'November'
                         break
                    case '12':
                         month = 'December'
                         break
              }

              return `${dateArray[2]} ${month} ${dateArray[0]}`
         },
         getMonthDiff(d1, d2){
              var months;
               months = (d2.getFullYear() - d1.getFullYear()) * 12;
               months -= d1.getMonth();
               months += d2.getMonth();
               return months <= 0 ? 0 : months;
         },
         getDayDiff(d1, d2){
              return Math.floor((Date.parse(d2) - Date.parse(d1)) / 86400000);
         },
         apply(){
              let date1 = new Date(this.dateStart)
              let date2 = new Date(this.dateEnd)
              if(this.statusPeriod === 'today' || this.statusPeriod === 'yesterday' || this.statusPeriod === 'thismonth'){
                   this.getDatetext()
                   this.dialog = false
                   return
              }
              
              if(this.getMonthDiff(date1, date2) > 6){
                   alert('Maximum range 6 months')
              } else if (this.getDayDiff(date1, date2) < 1 ){
                   alert('Minimum range 1 day and Input date in the valid order')
              }
              this.getDatetext()
              this.dialog = false
         }
         
    },
    mounted(){
         this.dateText = `${this.parseDate(this.dateStart)} - ${this.parseDate(this.dateEnd)}`
    }

}
</script>

<style scoped>
     @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&family=Roboto:wght@400;500&display=swap');

     *{
          font-family: 'Open Sans', sans-serif;
          text-transform: capitalize;

     }
     @media screen and (max-width: 600px) {
          .buttonPeriod{
               display: block;
               height: auto !important;
          }
     }
</style>