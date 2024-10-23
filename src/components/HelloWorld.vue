<template>
  <div id="app">
   <!-- Search Bar -->
   
     <!-- <v-autocomplete
      
      v-model="searchQuery"
   
     v-model:search="search"
     :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
   ></v-autocomplete> -->

   <v-text-field id="autocomplete" base-color="white" bg-color="white" style=" position: absolute; top: 10px; left: 60%; transform: translateX(-50%); z-index: 10; width: 50%;" v-model="searchQuery"   class="mx-auto"
     label="Search Location" clearable
      ></v-text-field>
 

   <!-- Google Map -->
   <div ref="map" class="mx-auto" id="map" style="height: 80vh; width: 89%;"></div>

   <!-- Sliders and Costs -->
   <v-container class="pa-4">
     <v-row class="mb-4" align="center">
       <v-col>
         <v-card>
           <v-card-title>
             <span class="headline">Panel Counts: {{ Math.trunc(panels) }}</span>
           </v-card-title>
           <v-card-actions>
             <v-slider
               v-model="panels"
               :max="max"
               :min="min"
               hide-details
               @update:model-value="buildPanels(respData)"
               color="primary"
             ></v-slider>
           </v-card-actions>
         </v-card>
       </v-col>
     </v-row>

     <v-row class="mb-4" align="center" >
       <v-col cols="4">
         <v-card>
           <v-card-title>
             <span class="headline">Cost in US (Without Solar):</span>
           </v-card-title>
           <v-card-text>
             <span class="display-1">{{ costWithoutSolar }} $</span>
           </v-card-text>
         </v-card>
       </v-col>
       <v-col cols="4">
         <v-card>
           <v-card-title>
             <span class="headline">Cost in US (With Solar):</span>
           </v-card-title>
           <v-card-text>
             <span class="display-1">{{ costWithSolar }} $</span>
           </v-card-text>
         </v-card>
       </v-col>
       <v-col cols="4">
         <v-card>
           <v-card-title>
             <span class="headline">Savings:</span>
           </v-card-title>
           <v-card-text>
             <span class="display-1">{{ savings }} $</span>
           </v-card-text>
         </v-card>
       </v-col>
       <v-col cols="6">
 <v-card class="pa-4" outlined elevation="2" color="#F5F5F5">
   <v-card-title class="headline font-weight-bold">
     Solar Potential Analysis
   </v-card-title>
   <v-divider class="my-2"></v-divider>
   <v-row class="align-center justify-center my-2" no-gutters>
     <v-col cols="4">
       <span class="title">Monthly Average Bill</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="Enter Bill Amount"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
         @blur="calculateCost"
         v-model="this.monthlyAverageEnergyBill"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   <v-row class="align-center justify-center my-2" no-gutters>
     <v-col cols="4">
       <span class="title">Energy Cost per KWH</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="Energy Cost per KWH<"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.energyCostPerKwh"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   <v-row class="align-center justify-center my-2" no-gutters>
     <v-col cols="4">
       <span class="title">Solar Incentives</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="Solar Incentive"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.solarIncentives"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   <v-row class="align-center justify-center my-2" no-gutters >
     <v-col cols="4">
       <span class="title">Installation cost per Watt</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="nstallation cost per Watt"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.installationCostPerWatt"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   <v-row class="align-center justify-center" no-gutters>
     <v-col cols="4">
       <span class="title">Panel Capacity</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="Panel Capacity"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.panelCapacityWatts"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   
 </v-card>
</v-col>
<v-col cols="6">
 <v-card class="pa-4" outlined elevation="2" color="#F5F5F5">
   <v-card-title class="headline font-weight-bold">
    Advanced Settings
   </v-card-title>
   <v-divider class="my-2"></v-divider>
   <v-row class="align-center justify-center my-2" no-gutters>
     <v-col cols="4">
       <span class="title">Installation Life Span</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="Installation Life Span"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.installationLifeSpan"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
   <v-row class="align-center justify-center my-2" no-gutters>
     <v-col cols="4">
       <span class="title">DC To Ac Rate</span>
     </v-col>
     <v-col cols="4">
       <v-text-field
        type="number"
         label="DC To Ac Rate"
         variant="outlined"
         prepend-inner-icon="mdi-currency-usd"
         color="primary"
         outlined
            @blur="calculateCost"
         v-model="this.dcToAcDerate"
         hide-details
       ></v-text-field>
     </v-col>
   </v-row>
 </v-card>
</v-col>
     </v-row>
   </v-container>
   <v-snackbar v-model="snackbar">
      {{ message }}
      <template v-slot:actions>
        <v-btn
          color="pink"
          variant="text"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
 </div>
</template>
<script>
export default {
 data() {
   return {
    snackbar: false,
    message:"",
     map: null, 
     panels: 4, 
     searchQuery:'',
     autoComplete:'',
     min:0,
     max:0,
     respData:null,
     costWithoutSolar : 0,
     costWithSolar:0,
     monthlyAverageEnergyBill:300,
     energyCostPerKwh:0.31,
     solarIncentives:7000,
     installationCostPerWatt:4.00,
     panelCapacityWatts:250,
     installationLifeSpan:20,
     dcToAcDerate:0.85,
     savings:0,
     solarPanelConfigs:[],
     polygonArray:[],
     lat:37.4449439,
     lng:-122.13914659999998,

   };
 },
 methods: {
   initAutocomplete(){
      this.autoComplete = new window.google.maps.places.Autocomplete(
       document.getElementById('autocomplete'),
       {
         types:['establishment'],
         fields:['place_id','geometry','name'],
       }
     )

      this.autoComplete.addListener('place_changed',this.onPlaceChanged)

   },
   async initMap() {
     console.log("Initializing map...");

     
     if (!window.google || !window.google.maps) {
      
       const script = document.createElement("script");
      
       const apiKey = process.env.VUE_APP_MAPS_API_KEY;
       script.src =
         `https://maps.googleapis.com/maps/api/js?key=${apiKey}&loading=async&libraries=geometry,places&callback=initMap`;
       script.async = true;
       script.defer = true;
       document.head.appendChild(script);

      
       window.initMap = () => {
         this.createMap();
       };
     } else {
      
       this.createMap();
     }
   },  
   createMap() {
     // Initialize the Google map
   
     this.map = new window.google.maps.Map(this.$refs.map, {
       center: { lat: this.lat, lng: this.lng },
       zoom: 20,
       mapTypeId: "satellite",
     });
     console.log(window?.google?.maps.places);



    
     this.getBuildingInsights();
     this.initAutocomplete();
   },
   calculateCost(){

             this.panelCapacityWatts = parseFloat(this.panelCapacityWatts);
             this.energyCostPerKwh = parseFloat(this.energyCostPerKwh);
             this.solarIncentives = parseFloat(this.solarIncentives);
             this.installationCostPerWatt = parseFloat(this.installationCostPerWatt);
             this.installationLifeSpan = parseFloat(this.installationLifeSpan);

              let yearlyEnergyDcKwh = 12000;

               let efficiencyDepreciationFactor = 0.995;
               let costIncreaseFactor = 1.022;
               let discountRate = 1.04;

               
               let installationSizeKw = (this.panels * this.panelCapacityWatts )/ 1000;
               

               let installationCostTotal = this.installationCostPerWatt * installationSizeKw * 1000;
           
               // Energy consumption   
               let monthlyKwhEnergyConsumption = this.monthlyAverageEnergyBill / this.energyCostPerKwh;
               let yearlyKwhEnergyConsumption = monthlyKwhEnergyConsumption * 12;

               // Energy produced for installation life span
               let initialAcKwhPerYear = yearlyEnergyDcKwh * this.dcToAcDerate;
               const solarPanelConfig = this.solarPanelConfigs?.find((ele)=>ele?.panelsCount == Math.trunc(this.panels));
               let panelCapacityRatio = this.panelCapacityWatts / this.respData.solarPotential.panelCapacityWatts;
               if(solarPanelConfig){
                 initialAcKwhPerYear =  solarPanelConfig.yearlyEnergyDcKwh*panelCapacityRatio*this.dcToAcDerate;
               }

               let yearlyProductionAcKwh = [...Array(this.installationLifeSpan).keys()].map(
                   (year) => {
                     return initialAcKwhPerYear * efficiencyDepreciationFactor ** year}
               );

               // Cost with solar for installation life span
               let yearlyUtilityBillEstimates = yearlyProductionAcKwh.map(
               (yearlyKwhEnergyProduced, year) => {
                   const billEnergyKwh = yearlyKwhEnergyConsumption - yearlyKwhEnergyProduced;
                   const billEstimate =
                   (billEnergyKwh * this.energyCostPerKwh * costIncreaseFactor ** year) / discountRate ** year;
                   return Math.max(billEstimate, 0); // bill cannot be negative
               },
               );

             

               let remainingLifetimeUtilityBill = yearlyUtilityBillEstimates.reduce((x, y) => x + y, 0);
            
               let totalCostWithSolar = installationCostTotal + remainingLifetimeUtilityBill - this.solarIncentives;
               console.log(`Cost with solar: $${totalCostWithSolar.toFixed(2)}`);
               this.costWithSolar = totalCostWithSolar.toFixed(2);

               // Cost without solar for installation life span

               
               let yearlyCostWithoutSolar = [...Array(this.installationLifeSpan).keys()].map((year) => {
               return (this.monthlyAverageEnergyBill * 12 * costIncreaseFactor ** year) / discountRate ** year;
             });

               
               let totalCostWithoutSolar = yearlyCostWithoutSolar.reduce((x, y) => x + y, 0);
               console.log(`Cost without solar: $${totalCostWithoutSolar.toFixed(2)}`);
               this.costWithoutSolar = totalCostWithoutSolar.toFixed(2);

               // Savings with solar for installation life span
               this.savings = (totalCostWithoutSolar - totalCostWithSolar).toFixed(2);
               console.log(`Savings: $${this.savings} in ${this.installationLifeSpan} years`);

   },
   buildPanels(data){
     console.log("running this ",data);
     if ( data && data.solarPotential) {
       if(this.polygonArray.length) this.removePolygons();
       
         const solarPotential = data.solarPotential;
         this.max = data.solarPotential.maxArrayPanelsCount;
         
         data.solarPotential.solarPanels.forEach((panel, index) => {
           if (index >= this.panels) return;

           const [w, h] = [solarPotential.panelWidthMeters / 2, solarPotential.panelHeightMeters / 2];
           const points = [
             { x: +w, y: +h }, // top right
             { x: +w, y: -h }, // bottom right
             { x: -w, y: -h }, // bottom left
             { x: -w, y: +h }, // top left
             { x: +w, y: +h }, // top right (to close the polygon)
           ];

           const orientation = panel.orientation === 'PORTRAIT' ? 90 : 0;
           const azimuth = solarPotential.roofSegmentStats[panel.segmentIndex].azimuthDegrees;

           // Create a polygon for each solar panel
          
           const polygon = new window.google.maps.Polygon({
             paths: points.map(({ x, y }) =>
               window.google.maps.geometry.spherical.computeOffset(
                 { lat: panel.center.latitude, lng: panel.center.longitude },
                 Math.sqrt(x * x + y * y),
                 Math.atan2(y, x) * (180 / Math.PI) + orientation + azimuth,
               )
             ),
             strokeColor: 'black',
             strokeOpacity: 0.9,
             strokeWeight: 1,
             fillColor: 'gray',
             fillOpacity: 0.9,
           });

           // Add the polygon to the map
           polygon.setMap(this.map);
           this.polygonArray.push(polygon);
         });

       
              
        this.calculateCost();

       }

   },
   removePolygons(){
     this.polygonArray.forEach((polygon)=>{
       polygon.setMap(null);

     })
     this.polygonArray = [];
   },
   async getBuildingInsights() {
     try {
       const args = {
         'location.latitude': this.lat.toFixed(5),
         'location.longitude': this.lng.toFixed(5),
       };
      const apiKey = process.env.VUE_APP_MAPS_API_KEY;
       const params = new URLSearchParams({ ...args, key: apiKey });
       const response = await fetch(
         `https://solar.googleapis.com/v1/buildingInsights:findClosest?${params}`, {
           headers: {
             'content-type': 'application/json',
           },
         }
       );
       const result = await response.json();
       if(result?.error){
        console.log(result);
         this.snackbar = true;
         this.message = result?.error.message;
         console.log("show error");
       }else{
        this.map.setCenter({lat:this.lat,lng:this.lng});
        this.respData = result;
       console.log("this is result",this.respData);

       this.solarPanelConfigs = result?.solarPotential.solarPanelConfigs;
       this.buildPanels(result);

       }
      
       
     } catch (error) {
       console.error("Error fetching building insights:", error);
     }
   },
   onPlaceChanged(){
     // console.log("this is data",place);
     var place = this.autoComplete.getPlace();
     if(!place.geometry){
       console.log("there is not place geometry");
     }else{
       console.log(place.geometry.location.lat());
       this.lat = place.geometry.location.lat();
       this.lng = place.geometry.location.lng();
       this.getBuildingInsights();
    
       
     }
   }
 },
 mounted(){
   this.initMap();
   // this.initAutocomplete();
   // this.autoComplete.addEventListener('place_change',this.onPlaceChanged)
  
 },
 // created() {
 //   this.initMap(); // Initialize the map when the component is created
 // },
};
</script>

<style scoped>
.headline {
 font-weight: bold;
 font-size: 1rem;
}
.display-1 {
 font-size: 1.2rem;
 font-weight: bold;
}
</style>
