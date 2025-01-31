<template>
  <div class="home">
    <div class="op-container d-flex px-4 py-2">
      <span class="mt-2 mx-2">SEATTLE, WA 98101, USA </span> <button type="button" @click="assignCarriers"
        class="btn btn-primary">load</button>
    </div>

    <div ref="map" class="mx-auto" id="map" style="height: 80vh; width: 95%;"></div>
    <div v-if="carrierAssigned" class="card list-wrap">

      <div class="heading">
        <span> Lit Buildings</span>
        <div class="sub-heading">
          <span>{{ carrierData.site[0].city }}, {{ carrierData.site[0].state }}, {{ carrierData.site[0].zipcode }}
          </span>
          <span>{{ carrierData.count }}</span>
        </div>
      </div>
      <hr>
      <div class="legend-wrap px-2 py-1 mb-4">
        <span>Legends</span>
        <div class="d-flex justify-content-between">
          <div class="legend-icon">
            <div class="circle mr-2" style="background-color:#5fe75f;"></div>
            <span style="font-size: 13px;">OnNet</span>
          </div>
          <div>
            <div class="circle mr-2" style="background-color: #f19b2a;"></div>
            <span style="font-size: 13px;">NearNet</span>
          </div>
          <div class="d-flex flex-column">
            <i class="fa-solid fa-network-wired" style="font-size: 32px;"></i>
            <span class="mt-2 ml-2" style="font-size: 13px;">fiber</span>
          </div>
          <div class="d-flex flex-column">
            <i class="fa fa-wifi" style="font-size: 32px;"></i>
            <span class="mt-2 " style="font-size: 13px;">wireless</span>
          </div>

        </div>


      </div>
      <hr>

      <div v-for="(cData, index) in carrierData.site" :key="index">
        <div class="site-wrap">
          <div class="site-heading">
            <strong>{{ cData.street }}</strong>
            <span>{{ cData.city }}, {{ cData.state }}, {{ cData.zipcode }}</span>
          </div>
          <div class="site-info">
            <span> Distance : {{ cData.distance_int }}</span>
            <span> Carrier count : {{ cData.carrier_count }}</span>
          </div>
        </div>

        <div v-for="(carriedData, index) in cData.carriers" :key="index">
          <div class="site-carrier px-2 py-2">
            <div class="carrier-name ">
              <i class="fa fa-wifi" style="color:#f19b2a" v-if="carriedData.xnet_code == 'N'"> </i>
              <i class="fa fa-wifi" style="color: green;" v-else></i>
              <span class="ml-2  font-weight-bold"> <ins>{{ carriedData.carriername }}</ins></span>
            </div>
            <div class="carrier-type">
              {{ carriedData.carriertype }}
            </div>


          </div>
          <hr v-if="index != cData.carriers.length - 1" style="width: 100%; margin-bottom: -2px; margin-top: -2px;">
        </div>

      </div>

    </div>
  </div>
</template>

<script>


export default {
  name: 'HomeView',

  data() {
    return {
      lat: 37.4449439,
      lng: -122.13914659999998,
      carrierAssigned: false,
      carrierData: {
        "status": "OK",
        "count": "100",
        "version": "2.03",
        "site": [
          {
            "method": "geo",
            "distance": "100",
            "distance_int": 100,
            "street": "1313 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1313 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6084978001756,
            "longitude": -122.335612004346,
            "markerid": 1,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "100",
            "distance_int": 100,
            "street": "1315 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1315 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6085378001822,
            "longitude": -122.335662004347,
            "markerid": 2,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "105",
            "distance_int": 105,
            "street": "1309 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1309 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6083778001557,
            "longitude": -122.335542004345,
            "markerid": 3,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "1321 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1321 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608692,
            "longitude": -122.335885,
            "markerid": 4,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "1325 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1325 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608692,
            "longitude": -122.335885,
            "markerid": 5,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "AT&T",
                "carrierid": "1",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 5
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "315 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "315 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608692,
            "longitude": -122.335885,
            "markerid": 6,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "1319 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1319 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608692,
            "longitude": -122.335885,
            "markerid": 7,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "1329 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1329 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608692,
            "longitude": -122.335885,
            "markerid": 8,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "125",
            "distance_int": 125,
            "street": "1323 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1323 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6086678002044,
            "longitude": -122.335802004349,
            "markerid": 9,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "150",
            "distance_int": 150,
            "street": "1333 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1333 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608784,
            "longitude": -122.335873,
            "markerid": 10,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "151",
            "distance_int": 151,
            "street": "303 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "303 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608636,
            "longitude": -122.336792,
            "markerid": 11,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "164",
            "distance_int": 164,
            "street": "216 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "216 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6087478002162,
            "longitude": -122.337362004375,
            "markerid": 12,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "184",
            "distance_int": 184,
            "street": "1402 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1402 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6088495768,
            "longitude": -122.33687484,
            "markerid": 13,
            "carriers": [
              {
                "carriername": "AT&T",
                "carrierid": "1",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Atlas Networks",
                "carrierid": "1360",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Verizon (XO)",
                "carrierid": "31",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 6
          },
          {
            "method": "geo",
            "distance": "204",
            "distance_int": 204,
            "street": "200 UNIVERSITY ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "200 UNIVERSITY ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6081378001164,
            "longitude": -122.337012004369,
            "markerid": 14,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "205",
            "distance_int": 205,
            "street": "1301 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1301 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6080478001014,
            "longitude": -122.336162004355,
            "markerid": 15,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "208",
            "distance_int": 208,
            "street": "1403 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1403 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60886,
            "longitude": -122.337441,
            "markerid": 16,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "236",
            "distance_int": 236,
            "street": "304 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "304 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609015,
            "longitude": -122.336737,
            "markerid": 17,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "236",
            "distance_int": 236,
            "street": "1404 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1404 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609015,
            "longitude": -122.336737,
            "markerid": 18,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "236",
            "distance_int": 236,
            "street": "306 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "306 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609015,
            "longitude": -122.336737,
            "markerid": 19,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "236",
            "distance_int": 236,
            "street": "1400 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1400 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609015,
            "longitude": -122.336737,
            "markerid": 20,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "236",
            "distance_int": 236,
            "street": "310 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "310 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609015,
            "longitude": -122.336737,
            "markerid": 21,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "271",
            "distance_int": 271,
            "street": "1201 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1201 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6077809429,
            "longitude": -122.336094095,
            "markerid": 22,
            "carriers": [
              {
                "carriername": "Cogent Communications",
                "carrierid": "976",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "AT&T",
                "carrierid": "1",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 6
          },
          {
            "method": "geo",
            "distance": "271",
            "distance_int": 271,
            "street": "1305 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1305 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6078078000625,
            "longitude": -122.336042004353,
            "markerid": 23,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "401 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "401 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6092021373,
            "longitude": -122.335662004,
            "markerid": 24,
            "carriers": [
              {
                "carriername": "AT&T",
                "carrierid": "1",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 4
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "1415 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1415 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609225,
            "longitude": -122.336246,
            "markerid": 25,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "1401 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1401 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609225,
            "longitude": -122.336246,
            "markerid": 26,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "1405 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1405 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609225,
            "longitude": -122.336246,
            "markerid": 27,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "380 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "380 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609225,
            "longitude": -122.336246,
            "markerid": 28,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "277",
            "distance_int": 277,
            "street": "1411 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1411 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609225,
            "longitude": -122.336246,
            "markerid": 29,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 4
          },
          {
            "method": "geo",
            "distance": "296",
            "distance_int": 296,
            "street": "1406 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1406 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609223,
            "longitude": -122.336735,
            "markerid": 30,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "305",
            "distance_int": 305,
            "street": "1200 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1200 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.607711,
            "longitude": -122.335618,
            "markerid": 31,
            "carriers": [
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Verizon (XO)",
                "carrierid": "31",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Windstream",
                "carrierid": "19",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 6
          },
          {
            "method": "geo",
            "distance": "329",
            "distance_int": 329,
            "street": "1410 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1410 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609268,
            "longitude": -122.336822,
            "markerid": 32,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "329",
            "distance_int": 329,
            "street": "1416 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1416 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609343,
            "longitude": -122.336914,
            "markerid": 33,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "329",
            "distance_int": 329,
            "street": "1414 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1414 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609343,
            "longitude": -122.336914,
            "markerid": 34,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "347",
            "distance_int": 347,
            "street": "402 UNIVERSITY ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "402 UNIVERSITY ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608542,
            "longitude": -122.334653,
            "markerid": 35,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "348",
            "distance_int": 348,
            "street": "1305 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1305 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6083778001567,
            "longitude": -122.335022004337,
            "markerid": 36,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "349",
            "distance_int": 349,
            "street": "412 UNIVERSITY ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "412 UNIVERSITY ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60859,
            "longitude": -122.334559,
            "markerid": 37,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "354",
            "distance_int": 354,
            "street": "1301 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1301 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608274,
            "longitude": -122.335362,
            "markerid": 38,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "354",
            "distance_int": 354,
            "street": "314 UNIVERSITY ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "314 UNIVERSITY ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608274,
            "longitude": -122.335362,
            "markerid": 39,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "355",
            "distance_int": 355,
            "street": "1306 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1306 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6086778002056,
            "longitude": -122.33525200434,
            "markerid": 40,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "355",
            "distance_int": 355,
            "street": "1304 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1304 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6087078002108,
            "longitude": -122.335052004337,
            "markerid": 41,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "362",
            "distance_int": 362,
            "street": "1412 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1412 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609353,
            "longitude": -122.33683,
            "markerid": 42,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "363",
            "distance_int": 363,
            "street": "400 UNIVERSITY ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "400 UNIVERSITY ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6082478001342,
            "longitude": -122.334862004334,
            "markerid": 43,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "364",
            "distance_int": 364,
            "street": "1308 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1308 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60883101,
            "longitude": -122.334973,
            "markerid": 44,
            "carriers": [
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "377",
            "distance_int": 377,
            "street": "1310 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1310 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6088778002374,
            "longitude": -122.335042004337,
            "markerid": 45,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "377",
            "distance_int": 377,
            "street": "1314 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1314 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6088978002411,
            "longitude": -122.335420043441,
            "markerid": 46,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "381",
            "distance_int": 381,
            "street": "1413 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1413 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6094878003381,
            "longitude": -122.336412004359,
            "markerid": 47,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "381",
            "distance_int": 381,
            "street": "1417 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1417 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6095478003474,
            "longitude": -122.336420043611,
            "markerid": 48,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Atlas Networks",
                "carrierid": "1360",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 6
          },
          {
            "method": "geo",
            "distance": "381",
            "distance_int": 381,
            "street": "400 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "400 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609522,
            "longitude": -122.335577,
            "markerid": 49,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "381",
            "distance_int": 381,
            "street": "1404 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1404 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609522,
            "longitude": -122.335577,
            "markerid": 50,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "381",
            "distance_int": 381,
            "street": "1400 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1400 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609522,
            "longitude": -122.335577,
            "markerid": 51,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1319 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1319 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 52,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1323 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1323 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 53,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1327 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1327 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 54,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "411 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "411 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 55,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1341 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1341 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 56,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1350 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1350 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 57,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1318 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1318 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 58,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1315 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1315 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 59,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1320 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1320 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 60,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1330 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1330 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 61,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "505 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "505 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609039,
            "longitude": -122.334785,
            "markerid": 62,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "405 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "405 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 63,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "407 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "407 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 64,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "409 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "409 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 65,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1305 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1305 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 66,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1335 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1335 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 67,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1312 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1312 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 68,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1333 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1333 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 69,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "393",
            "distance_int": 393,
            "street": "1331 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1331 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.608961,
            "longitude": -122.334807,
            "markerid": 70,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "394",
            "distance_int": 394,
            "street": "1401 2ND AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1401 2ND AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6083678001542,
            "longitude": -122.338482004393,
            "markerid": 71,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "394",
            "distance_int": 394,
            "street": "1400 2ND AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1400 2ND AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6085578001854,
            "longitude": -122.337882004383,
            "markerid": 72,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "399",
            "distance_int": 399,
            "street": "201 UNION ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "201 UNION ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6082780014125,
            "longitude": -122.337972004385,
            "markerid": 73,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "408",
            "distance_int": 408,
            "street": "1401 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1401 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6088178002284,
            "longitude": -122.33752004378,
            "markerid": 74,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "408",
            "distance_int": 408,
            "street": "1225 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1225 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6079478000856,
            "longitude": -122.335020043368,
            "markerid": 75,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "416",
            "distance_int": 416,
            "street": "1406 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1406 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60962,
            "longitude": -122.335861,
            "markerid": 76,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "416",
            "distance_int": 416,
            "street": "1408 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1408 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609613,
            "longitude": -122.335664,
            "markerid": 77,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "429",
            "distance_int": 429,
            "street": "1418 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1418 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60956,
            "longitude": -122.337151,
            "markerid": 78,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "429",
            "distance_int": 429,
            "street": "4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98181",
            "site_address": "4TH AVE,SEATTLE,WA,98181",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609586,
            "longitude": -122.336581,
            "markerid": 79,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "429",
            "distance_int": 429,
            "street": "1423 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1423 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6096478003646,
            "longitude": -122.336622004363,
            "markerid": 80,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "429",
            "distance_int": 429,
            "street": "1421 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1421 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6096,
            "longitude": -122.336527,
            "markerid": 81,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "429",
            "distance_int": 429,
            "street": "301 PIKE ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "301 PIKE ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60956,
            "longitude": -122.337153,
            "markerid": 82,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "451",
            "distance_int": 451,
            "street": "211 PIKE ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "211 PIKE ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609112,
            "longitude": -122.338306,
            "markerid": 83,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "451",
            "distance_int": 451,
            "street": "1215 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98161",
            "site_address": "1215 4TH AVE,SEATTLE,WA,98161",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60771,
            "longitude": -122.334801,
            "markerid": 84,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 4
          },
          {
            "method": "geo",
            "distance": "451",
            "distance_int": 451,
            "street": "1218 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1218 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60765,
            "longitude": -122.335401,
            "markerid": 85,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "451",
            "distance_int": 451,
            "street": "1221 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1221 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.607717800048,
            "longitude": -122.33523200434,
            "markerid": 86,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "451",
            "distance_int": 451,
            "street": "1215 4 AVE 2400 FINANCIAL CTR",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98161",
            "site_address": "1215 4 AVE 2400 FINANCIAL CTR,SEATTLE,WA,98161",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.607715,
            "longitude": -122.334805,
            "markerid": 87,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "458",
            "distance_int": 458,
            "street": "1212 2ND AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1212 2ND AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6072777999751,
            "longitude": -122.336732004365,
            "markerid": 88,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "458",
            "distance_int": 458,
            "street": "1301 2ND AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1301 2ND AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6073132614,
            "longitude": -122.337205482,
            "markerid": 89,
            "carriers": [
              {
                "carriername": "AT&T",
                "carrierid": "1",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Cogent Communications",
                "carrierid": "976",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "NoaNet",
                "carrierid": "1354",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 5
          },
          {
            "method": "geo",
            "distance": "470",
            "distance_int": 470,
            "street": "1430 2ND AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1430 2ND AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.6092004,
            "longitude": -122.338354264199,
            "markerid": 90,
            "carriers": [
              {
                "carriername": "Atlas Networks",
                "carrierid": "1360",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 3
          },
          {
            "method": "geo",
            "distance": "487",
            "distance_int": 487,
            "street": "1414 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1414 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60983,
            "longitude": -122.336051,
            "markerid": 91,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "491",
            "distance_int": 491,
            "street": "1423 3RD AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1423 3RD AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60932,
            "longitude": -122.337811,
            "markerid": 92,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "499",
            "distance_int": 499,
            "street": "1425 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1425 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.60979,
            "longitude": -122.336661,
            "markerid": 93,
            "carriers": [
              {
                "carriername": "Lumen",
                "carrierid": "1811",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "Telco",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "O",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 4
          },
          {
            "method": "geo",
            "distance": "499",
            "distance_int": 499,
            "street": "315 PIKE ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "315 PIKE ST,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609826,
            "longitude": -122.337229,
            "markerid": 94,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "499",
            "distance_int": 499,
            "street": "1429 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1429 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Nearby Match - less than 500 ft",
            "latitude": 47.609773,
            "longitude": -122.336865,
            "markerid": 95,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              },
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 2
          },
          {
            "method": "geo",
            "distance": "513",
            "distance_int": 513,
            "street": "213 PIKE ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "213 PIKE ST,SEATTLE,WA,98101",
            "match_level": "Sites over 500 feet",
            "latitude": 47.60944201,
            "longitude": -122.338122,
            "markerid": 96,
            "carriers": [
              {
                "carriername": "Zayo",
                "carrierid": "26",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "532",
            "distance_int": 532,
            "street": "1403 5TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1403 5TH AVE,SEATTLE,WA,98101",
            "match_level": "Sites over 500 feet",
            "latitude": 47.609624,
            "longitude": -122.334807,
            "markerid": 97,
            "carriers": [
              {
                "carriername": "Comcast",
                "carrierid": "5",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "CableCo",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "533",
            "distance_int": 533,
            "street": "1427 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1427 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Sites over 500 feet",
            "latitude": 47.6098678003994,
            "longitude": -122.336612004363,
            "markerid": 98,
            "carriers": [
              {
                "carriername": "Zayo (Allstream)",
                "carrierid": "25",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "533",
            "distance_int": 533,
            "street": "319 PIKE ST",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "319 PIKE ST,SEATTLE,WA,98101",
            "match_level": "Sites over 500 feet",
            "latitude": 47.609915,
            "longitude": -122.336867,
            "markerid": 99,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          },
          {
            "method": "geo",
            "distance": "533",
            "distance_int": 533,
            "street": "1431 4TH AVE",
            "city": "SEATTLE",
            "state": "WA",
            "zipcode": "98101",
            "site_address": "1431 4TH AVE,SEATTLE,WA,98101",
            "match_level": "Sites over 500 feet",
            "latitude": 47.609926,
            "longitude": -122.336777,
            "markerid": 100,
            "carriers": [
              {
                "carriername": "Astound Business Solutions",
                "carrierid": "895",
                "xnet_code": "N",
                "xnet_service": "F",
                "carriertype": "DLEC",
                "datacenter": null,
                "tower": null
              }
            ],
            "carrier_count": 1
          }
        ]
      },
      wiredServices: ['Telco', 'CableCo', 'DataCenter', 'CLEC', 'DLEC'],

    }
  },

  methods: {
    createMap() {
      this.map = new window.google.maps.Map(this.$refs.map, {
        center: { lat: this.carrierData.site[0].latitude, lng: this.carrierData.site[0].longitude },
        zoom: 17,
        mapId: '10',
        mapTypeId: 'roadmap'
      });
      // this.assignCarriers();
    },

    async initMap() {
      console.log("Initializing map...");
      if (!window.google || !window.google.maps) {
        const script = document.createElement("script");
        const apiKey = process.env.VUE_APP_MAPS_API_KEY;
        script.src = `https://maps.googleapis.com/maps/api/js?key=${apiKey}&loading=async&libraries=geometry,places,marker&callback=initMap`;
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

    async assignCarriers() {
      const { AdvancedMarkerElement } = await window.google.maps.importLibrary("marker");

      this.carrierData.site.forEach((cData) => {
        const position = new window.google.maps.LatLng(cData.latitude, cData.longitude);
        cData.isOpen = false;
        const marker = new AdvancedMarkerElement({
          map: this.map,
          position: position,
          title: cData.site_address,
          // content: this.buildContent(cData),
        });

        marker.content = this.buildContent(cData, marker);

        marker.addListener("click", () => {
          this.toggleHighlight(marker);

        });
      });
      this.carrierAssigned = true;
    },

    buildContent(wifiSite, marker) {
      const content = document.createElement("div");
      content.classList.add("wifiSite");
      console.log(wifiSite);
      let carrier = wifiSite.carriers[0];
      console.log(this.wiredServices.includes(carrier.carriertype));
      content.innerHTML = `
      <div class="icon">
       ${this.wiredServices.includes(carrier.carriertype) ?
          `${carrier.xnet_code == 'O' ?
            ` <i  aria-hidden="true" class="fa-solid fa-network-wired green" style="background-color:#5fe75f;color:black;z-index:0" ></i>
          <span class="fa-sr-only">${wifiSite?.site_address}</span>` :
            ` <i  aria-hidden="true" style="background-color: #f19b2a;color:black;z-index:0" class="fa-solid fa-network-wired yellow" ></i>
          <span class="fa-sr-only">${wifiSite?.site_address}</span>`}` : `${carrier.xnet_code == 'O' ?
            ` <i  aria-hidden="true" class="fa fa-wifi green" style="background-color:#5fe75f;color:black;z-index:0" ></i>
          <span class="fa-sr-only">${wifiSite?.site_address}</span>` :
            ` <i  aria-hidden="true" style="background-color: #f19b2a;color:black;z-index:0" class="fa fa-wifi yellow" ></i>
          <span class="fa-sr-only">${wifiSite?.site_address}</span>`}`}
        
         
      </div>
      <div class="details">
        <div class="d-flex justify-space-between">

         <img src="https://img.icons8.com/emoji/48/000000/globe-showing-americas-emoji.png" alt="Map" width="24" />
         <i class="fa-regular fa-circle-xmark"  style="font-size:15px" ></i>
         </div>

             <div class="info-window card">
          <div style="display: flex; align-items: center;">
           
            <strong style="margin-left: 8px;">${wifiSite.site_address}</strong>
          </div>
          <p>We found (${wifiSite.carrier_count}) carrier at this location</p>

          ${wifiSite.carriers.map((carrier) => {
              return ` <div  >
          <strong style="color: #85c2f3;;">${carrier.carriername}</strong> 
             (${carrier.xnet_code == 'O' ? 'OnNet' : 'NerNet'})
          </div>`
            })
        }
        </div>
       <button class="request-pricing-btn" >Requet Pricing</button>
          </div>
      </div>
    `;
      const button = content.querySelector(".request-pricing-btn");
      button.addEventListener("click", (e) => {
        e.stopPropagation();
        e.preventDefault();
        this.handleClick(wifiSite)
      });
      const closeButton = content.querySelector('.fa-circle-xmark');
      closeButton.addEventListener('click', (e) => {
        e.stopPropagation();
        e.preventDefault();
        content.classList.remove("highlight");
        marker.zIndex = null;
        content.querySelector('.icon').style.display = "block";

      });

      return content;
    },


    toggleHighlight(marker) {
      // if (marker.content.classList.contains("highlight")) {
      //   marker.content.classList.remove("highlight");
      //   marker.zIndex = null;
      //   marker.content.querySelector('.icon').style.display = "block";

      // } else {
      marker.content.classList.add("highlight");
      marker.zIndex = 1;
      marker.content.querySelector('.icon').style.display = "none";

      // }
    },
    handleClick(wifiSite) {
      console.log(`Requesting pricing for: ${wifiSite.site_address}`);
      alert(`Requesting pricing for ${wifiSite.site_address}`);

    }
  },

  mounted() {
    this.initMap();
    window.handleClick = this.handleClick;
    console.log(window.handleClick);
  },


}
</script>
<style>
:root {
  --building-color: #FF9800;
  --house-color: #0288D1;
  --shop-color: #7B1FA2;
  --warehouse-color: #558B2F;
}

/*
 * Optional: Makes the sample page fill the window.
 */

.home {
  width: 90%;

  margin: auto;
}

html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
}

/*
 * Always set the map height explicitly to define the size of the div element
 * that contains the map.
 */
#map {
  height: 100%;
  width: 100%;
}

/*
 * wifiSite styles in unhighlighted state.
 */
.wifiSite {
  /* align-items: center; */
  background-color: #FFFFFF;
  border: 2px solid gray;
  border-radius: 50%;
  color: #263238;
  display: flex;
  font-size: 14px;
  gap: 15px;
  height: 30px;
  justify-content: center;
  padding: 4px;
  position: relative;
  position: relative;
  transition: all 0.3s ease-out;
  width: 30px;
}


.wifiSite .icon {
  align-items: center;
  display: flex;
  justify-content: center;
  color: #FFFFFF;


}

.wifiSite .icon svg {
  height: 20px;
  width: auto;
}

.wifiSite .details {
  display: none;
  flex-direction: column;
  flex: 1;
  text-align: left;
}

.wifiSite .address {
  color: #9E9E9E;
  font-size: 10px;
  margin-bottom: 10px;
  margin-top: 5px;
}

.wifiSite .features {
  align-items: flex-end;
  display: flex;
  flex-direction: row;
  gap: 10px;
}

.wifiSite .features>div {
  align-items: center;
  background: #F5F5F5;
  border-radius: 5px;
  border: 1px solid #ccc;
  display: flex;
  font-size: 10px;
  gap: 5px;
  padding: 5px;
}

/*
 * wifiSite styles in highlighted state.
 */
.wifiSite.highlight {
  background-color: #FFFFFF;
  border-radius: 8px;
  box-shadow: 10px 10px 5px rgba(0, 0, 0, 0.2);
  height: fit-content;
  padding: 8px 15px;
  width: 350px;
}

.wifiSite.highlight::after {
  border-top: 9px solid #FFFFFF;
}

.wifiSite.highlight .details {
  display: flex;
}

.wifiSite.highlight .icon svg {
  width: 50px;
  height: 50px;
}

.list-wrap {
  /* border: 2px solid black; */

  width: 390px;

  position: absolute;
  max-height: 70vh;
  overflow-y: auto;
  top: 14%;
  right: 5.9%;

}

.heading {
  text-align: left;
  font-size: 20px;
  padding: 2px 10px;
  font-weight: 600;
}

.site-wrap {
  background-color: #85c2f3;
  height: 60px;
  padding: 10px 10px;
  text-align: left;
}

.site-heading {
  width: 60%;
  display: flex;
  flex-direction: column;
}

.site-info {
  width: 40%;
  text-align: right;
  display: flex;
  flex-direction: column;
  font-size: 13x;
}

.site-wrap {

  display: flex;
  flex-direction: row;
}

.site-carrier {
  display: flex;
  flex-direction: row;

  margin-top: 3px;


}

.carrier-name {
  text-align: left;
  width: 70%;
}

.carrier-type {
  width: 30%;
  text-align: right;
}

.sub-heading {
  display: flex;
  justify-content: space-between;
  padding: 2px 1px;
  font-size: 15px;
}

.legend-wrap {
  width: 70%;
  min-height: 90px;
  text-align: left;
}

.circle {
  margin-top: 4px;
  height: 30px;
  width: 30px;
  border-radius: 50%;
  background-color: #5fe75f;
}





.wifiSite:not(.highlight):has(.green) {
  background-color: #5fe75f;
}

.wifiSite:not(.highlight):has(.yellow) {
  background-color: #FF9800;
}

.property:not(.highlight):has(.fa-wifi .green)::after {
  border-top: 9px solid green;
}

.info-window {
  font-family: Arial, sans-serif;
  font-size: 14px;
  padding: 8px;
  border: 1px solid black;
}
</style>
