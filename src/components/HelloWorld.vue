<template>
  <div id="app">
    <h3>Average Number of Visitors :- {{ numberofvisitors }} </h3>
    <h3>Average Website Conversion Rate :- {{ avgwebsite }} %</h3>
    <h3>Average Transaction Value :- {{ avgtransaction }} £</h3>
    <h3>Increase in Conversion Rate Needed :- {{ slider }} %</h3>
    <input id="id-numberofvisitors" name="numberofvisitors" type="text" autocomplete="off" v-model="numberofvisitors"
      class="input" placeholder="Average Number of Visitors" />
    <input id="id-avgwebsite" name="avgwebsite" type="text" autocomplete="off" v-model="avgwebsite" class="input"
      placeholder="Average Website Conversion Rate" />
    <input id="id-avgtransaction" name="avgtransaction" type="text" autocomplete="off" v-model="avgtransaction"
      class="input" placeholder="Average Transaction Value" />
    <input id="id-convrate" name="convrate" type="range" min="0" max="100" v-model="slider" class="inputSlider" />
    <br>
    <button type="button" class="id-button" @click="webConversionResults()">Calculate</button>

    <div id="web_conversion_results">
      <div class="form-base">
        <div class="html-block html-block--theme-beta is-theme-beta">
          <div>
            <p>Incremental profit and revenue gains from new
              conversion rate:</p>
          </div>
        </div>
      </div>
      <div class="table-responsive">
        <table id="web_conversion_table" class="table table-bordered">
          <thead>
            <tr>
              <th></th>
              <th>Old Website</th>
              <th>Optimized Website</th>
              <th
                style="background-color: rgb(236, 255, 236); border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0); border-top-width: 1px; border-top-style: solid; border-top-color: rgb(0, 153, 0);">
                Incremental Benefit</th>
            </tr>
          </thead>
          <tbody>
            <tr class="output-row" style="background-color: rgb(249, 249, 251);">
              <td>Your visitors</td>
              <td>{{ child_0_1 }}</td>
              <td>{{ child_0_2 }}</td>
              <td
                style="background-color: rgb(230, 249, 232); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0);">
              </td>
            </tr>
            <tr class="output-row">
              <td>Website Conversions</td>
              <td>{{ child_1_1 }} %</td>
              <!-- <td>0%</td> -->
              <td>{{ optimizedWeb }}</td>
              <td
                style="background-color: rgb(236, 255, 236); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0);">
                {{ child_1_3 }} %</td>
            </tr>
            <tr class="output-row" style="background-color: rgb(249, 249, 251);">
              <td>Number of sales</td>
              <td>{{child_2_1}}</td>
              <td>{{child_2_2}}</td>
              <td
                style="background-color: rgb(230, 249, 232); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0);">
                {{child_2_3}}</td>
            </tr>
            <tr class="output-row">
              <td>Revenue</td>
              <td>£ {{child_3_1}}</td>
              <td>£ {{child_3_2}}</td>
              <td
                style="background-color: rgb(236, 255, 236); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0);">
                £ {{child_3_3}}</td>
            </tr>
            <tr class="output-row" style="background-color: rgb(249, 249, 251);">
              <td>Revenue per visitor</td>
              <td>£ {{child_4_1}}</td>
              <td>£ {{child_4_2}}</td>
              <td
                style="background-color: rgb(230, 249, 232); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0);">
                £ {{child_4_3}}</td>
            </tr>
            <tr class="output-row">
              <td>Visitors per transaction</td>
              <td>{{child_5_1}}</td>
              <td>{{child_5_2}}</td>
              <td id="bottom_rounder_corner"
                style="background-color: rgb(236, 255, 236); color: rgb(0, 153, 0); font-weight: bold; border-left-width: 1px; border-left-style: solid; border-left-color: rgb(0, 153, 0); border-right-width: 1px; border-right-style: solid; border-right-color: rgb(0, 153, 0); border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: rgb(0, 153, 0);">
                {{child_5_3}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

</template>

<script>
import { ref } from 'vue'
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    setup() {
      var optimizedWeb = '';
      var slider = ref('');
      var numberofvisitors = ref('');
      var avgwebsite = ref('');
      var avgtransaction = ref('');
      var e = false;
      function querySelector(elementClassId) {
        return document.querySelector(elementClassId);
      }

      function roundHundredth(a) {
        return Math.round(100 * a) / 100;
      }


      // Provide the parameters
      function displayErrorModal() {

      }

      function customslider() {
        (slider.value)/100;
      }

      function visitors() {
        numberofvisitors.value;
      }

      function website() {
        (avgwebsite.value)/100;
      }

      function transaction() {
        (avgtransaction.value);
      }

      var q = "";
      var A = "";
      var n = 0;
      var o = visitors;
      var u = website;
      var y = o * u;
      var l = y * transaction;
      var w = website * (1 + customslider);
      var k = '';
      var d = o * w;
      var a = d * transaction;
      var s = w * u;
      var h = d - y;
      var g = a - l;

      var z = l / o ;
      var m = o / y;
      var p = a / o;
      var f = o / d;
      var t = (p - z) / z;
      var B = (f - m) / m;

      var getAllElements = document.querySelectorAll(".output-row");

      var child_0_1, child_0_2, child_1_1, child_1_3, child_2_1, child_2_2, child_2_3, child_3_1, child_3_2, child_3_3, child_4_1, child_4_2, child_4_3, child_5_1, child_5_2, child_5_3;

      function  webConversionResults() {
      console.log('test');
        if (e) {
        return false;
        }
        if (w > 1) {
        q = "Invalid input in your desired conversion rate increase";
        A = "A website conversion rate can't be superior to 100%, so we replace your input value by 100%. Please also consider that a 100% conversion rate is unlikely to happen.";
        displayErrorModal(q, A, true);
        w = 1;
        k = 1;
        for (var x = 1, j = 0; x <= 250; x++) {
                    if (j > 100) {
                        k = x - 1;
                        break
                    }
                    j = website * (1 + x)
        }
        k -= 100;
        // Code still to be written

        /* $("#web_conversion_slider").slider("destroy");
                $("#web_conversion_slider").slider({
                    create: function (i, C) {},
                    value: k,
                    min: 0,
                    max: 250,
                    slide: function (i, C) {
                        $("#web_conversion_amt").text(C.value)
                    },
                    stop: function (i, C) {
                        if ($("#web_conversion_results").css("visibility") != "hidden") {
                            webConversionResults()
                        }
                    }
                }); */
                // $("#web_conversion_amt").text(k)
        }

        child_0_1 = '0';
        child_0_2 = '0';
        console.log('child_0_1', child_0_1);
        child_1_1 = roundHundredth(u * 100) + "%";
        optimizedWeb = child_1_1 + "%";
        child_1_3 = "+" + roundHundredth(s * 100) + "%";
        child_2_1 = Math.round(y);
        child_2_2 = Math.round(d);
        child_2_3 = Math.round(h);
        child_3_1 = "&pound; " + l;
        child_3_2 = "&pound; " + roundHundredth(a);
        child_3_3 = "&pound; " + roundHundredth(g);
        child_4_1 = isNaN(roundHundredth(z)) ? "&pound; 0" : "&pound; " + roundHundredth(z);
        child_4_2 = isNaN(roundHundredth(p)) ? "&pound; 0" : "&pound; " + roundHundredth(p);
        child_4_3 = isNaN(roundHundredth(t * 100)) ? "+0%" : "+" + roundHundredth(t * 100) + "%";
        child_5_1 = isNaN(roundHundredth(m)) ? 0 : roundHundredth(m);
        child_5_2 = isNaN(roundHundredth(f)) ? 0 : roundHundredth(f);
        child_5_3 = isNaN(roundHundredth(B * 100)) ? "0%" : roundHundredth(B * 100) + "%";

        // for (var i = 0; i < getAllElements.length; i++) {
        //         var getAllChild = getAllElements[i].children;
        //         // No of Visitors
        //         if (i == 0) {
        //             getAllChild[1].innerHTML = o;
        //             getAllChild[2].innerHTML = o;
        //         // Website Conversion
        //         } else if (i == 1) {
        //             getAllChild[1].innerHTML = ;
        //             optimizedWeb = ;
        //             console.log(optimizedWeb);
        //             getAllChild[3].innerHTML = "+" + roundHundredth(s * 100) + "%";
        //         // No of Sales
        //         } else if (i == 2) {
        //             getAllChild[1].innerHTML = Math.round(y);
        //             getAllChild[2].innerHTML = Math.round(d);
        //             getAllChild[3].innerHTML = Math.round(h);
        //         // Revenue
        //         } else if (i == 3) {
        //             getAllChild[1].innerHTML = "&pound; " + l;
        //             getAllChild[2].innerHTML = "&pound; " + roundHundredth(a);
        //             getAllChild[3].innerHTML = "&pound; " + roundHundredth(g);
        //         // Revenue per Visitor 
        //         } else if (i == 4) {
        //             getAllChild[1].innerHTML = isNaN(roundHundredth(z)) ? "&pound; 0" : "&pound; " + roundHundredth(z);
        //             getAllChild[2].innerHTML = isNaN(roundHundredth(p)) ? "&pound; 0" : "&pound; " + roundHundredth(p);
        //             getAllChild[3].innerHTML = isNaN(roundHundredth(t * 100)) ? "+0%" : "+" + roundHundredth(t * 100) + "%";
        //         // Visitors per Transaction
        //         } else if (i == 5) {
        //             getAllChild[1].innerHTML = isNaN(roundHundredth(m)) ? 0 : roundHundredth(m);
        //             getAllChild[2].innerHTML = isNaN(roundHundredth(f)) ? 0 : roundHundredth(f);
        //             getAllChild[3].innerHTML = isNaN(roundHundredth(B * 100)) ? "0%" : roundHundredth(B * 100) + "%";
        //         }
        //     }

            
            querySelector("#web_conversion_results").style.display = "block";
            // if (w < 1) {
            //    $("html, body").animate({
            //          scrollTop: 500
            //    }, "slow", function () {})
            // }
            return false
           
      }
      

      return {
        optimizedWeb,
        slider,
        numberofvisitors,
        avgwebsite,
        avgtransaction,
        getAllElements,
        child_0_1, child_0_2, child_1_1, child_1_3, child_2_1, child_2_2, child_2_3, child_3_1, child_3_2, child_3_3, child_4_1, child_4_2, child_4_3, child_5_1, child_5_2, child_5_3,
        e,
        q,
        A,
        n,
        o,
        u,
        y,
        l,
        w,
        k,
        d,
        a,
        s,
        h,
        g,
        z,
        m,
        p,
        f,
        t,
        B,
        querySelector,
        roundHundredth,
        website,
        transaction,
        customslider,
        visitors,
        displayErrorModal,
        webConversionResults
      }
    },
    data() {
      return {
        
      };
    }, 
    methods: {
      
    },

    
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  input {
    margin: 20px;
    width: 60%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #000;
    border-radius: 4px;
    box-sizing: border-box;
  }

  input[type="range"] {
    margin: 20px;
    width: 60%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #000;
    border-radius: 4px;
    box-sizing: border-box;
  }

  h3 {
    margin: 25px 0 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }

  /* Table CSS */
    /* #web_conversion_results {
            margin-top: 25px;
            display: none;
            position: relative;
        } */

        .table-responsive {
            min-height: .01%;
            overflow-x: auto;
        }

        #web_conversion_results table#web_conversion_table {
            margin: 15px 0;
            padding: 0;
        }

        #web_conversion_results table {
            border-collapse: separate;
        }

        .table-bordered {
            border: 1px solid #ddd;
        }

        .table {
            width: 100%;
            max-width: 100%;
            margin-bottom: 20px;
        }

        table {
            background-color: transparent;
        }

        table {
            border-spacing: 0;
            border-collapse: collapse;
        }

        thead {
            display: table-header-group;
            vertical-align: middle;
            border-top-color: inherit;
            border-right-color: inherit;
            border-bottom-color: inherit;
            border-left-color: inherit;
        }

        tr {
            display: table-row;
            vertical-align: inherit;
            border-top-color: inherit;
            border-right-color: inherit;
            border-bottom-color: inherit;
            border-left-color: inherit;
        }

        #web_conversion_results table#web_conversion_table tr {
            padding: 0;
            margin: 0;
        }

        .table>caption+thead>tr:first-child>td,
        .table>caption+thead>tr:first-child>th,
        .table>colgroup+thead>tr:first-child>td,
        .table>colgroup+thead>tr:first-child>th,
        .table>thead:first-child>tr:first-child>td,
        .table>thead:first-child>tr:first-child>th {
            border-top: 0;
        }

        .table-bordered>thead>tr>td,
        .table-bordered>thead>tr>th {
            border-bottom-width: 2px;
        }

        .table-bordered>tbody>tr>td,
        .table-bordered>tbody>tr>th,
        .table-bordered>tfoot>tr>td,
        .table-bordered>tfoot>tr>th,
        .table-bordered>thead>tr>td,
        .table-bordered>thead>tr>th {
            border: 1px solid #ddd;
        }

        .table>thead>tr>th {
            vertical-align: bottom;
            border-bottom: 2px solid #ddd;
        }

        .table>tbody>tr>td,
        .table>tbody>tr>th,
        .table>tfoot>tr>td,
        .table>tfoot>tr>th,
        .table>thead>tr>td,
        .table>thead>tr>th {
            padding: 8px;
            line-height: 1.42857143;
            vertical-align: top;
            border-top: 1px solid #ddd;
        }

        #web_conversion_results table#web_conversion_table tr th {
            font-weight: bold;
            padding: 10px;
            text-align: center;
        }

        #web_conversion_table tr:nth-child(odd) {
            background-color: #F9F9FB;
        }

        #web_conversion_table tr th:nth-child(4) {
            background-color: #ECFFEC;
            border-left: 1px solid #009900;
            border-right: 1px solid #009900;
            border-top: 1px solid #009900;
        }

        #web_conversion_table tr td:nth-child(4) {
            color: #009900;
            font-weight: bold;
            background-color: #ECFFEC;
            border-left: 1px solid #009900;
            border-right: 1px solid #009900;
        }

        #web_conversion_table tr td:nth-child(even) {
            background-color: #E6F9E8;
        }

        #web_conversion_table tr:nth-child(6) td:nth-child(even) {
            border-bottom: 1px solid #009900;
        }
  /* Table CSS End */
</style>