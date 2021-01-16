<!-- html section -->
<template lang="html">

   <!-- This is where the output from the Vue #app is displayed -->
    <b-container style="color: #c2c2c2;" >

    
    <!-- ****************** FLOORPLAN IMAGE ****************** -->
    <template>
        <div id="floorplan" style="position:absolute; left: 100px; width: 1720px; top:66px; height:35em; background:url(../../src/images/groundfloor.PNG);">

            <!-- ****************** RELOAD PAGE BUTTON ****************** -->
            <div style="position:absolute; width:150px;  left:1550px; top:12px;" > <button style="color:grey; font-size:80% !important;" v-on:click="reloadPage()"> Reload Page </button></div> 



            <!-- ********************************************* GARDEN LIGHTING *************************************** -->
            <!-- ****************** LED SPOT LIGHTS ****************** Garden Wall BBQ -->
            <div style="position:absolute; left:590px;  top:48px; outline: none;"                      :style="{color:  light_table[0].brightness_value != 0? 'var(--led-on-colour)' : 'var(--led-off-colour)'}"      v-b-popover.click.blur.top="'Garden Wall'" tabindex="0" >  <i v-on:click="clickLight('Garden/BBQ Wall Lights')" class="fa fa-circle" ></i></div>
            <div style="position:absolute; left:614px;  top:45px;"    class="light_brightness" > <animated-number :value="light_lookup_hc2name('Garden/BBQ Wall Lights').brightness_value" :formatValue="formatToValue" :duration="duration" v-if="light_lookup_hc2name('Garden/BBQ Wall Lights').brightness_hide">  </div>

            <!-- ****************** RGBW LEDS *********************** Garden Bench -->
            <div style="position:absolute; left:500px;  top:403px; font-size:150%; outline: none;"    :style="{color:  light_table[1].brightness_value != 0? light_table[1].colour_value : 'var(--led-off-colour)'}"        v-b-popover.click.blur.top="'Garden Bench'" tabindex="0" >  <i v-on:click="clickLight('Garden/Garden Bench Lights')" class="fa fa-window-minimize"></i></div>
            <div style="position:absolute; left:532px;  top:412px"    class="light_brightness" > <animated-number :value="light_lookup_hc2name('Garden/Garden Bench Lights').brightness_value" :formatValue="formatToValue" :duration="duration" v-if="light_lookup_hc2name('Garden/Garden Bench Lights').brightness_hide"> </div>





        </div>
    </template>




    <!-- ****************** USER SELECTION - LIGHTING GROUPS ****************** -->
    <!-- ****************** USER SELECTION - LIGHTING GROUPS ****************** -->
    <template id = "lighting group and preset light level shortcuts" >
        <div class="input-card" style="position:absolute; width:310px; height:450px; left:310px;  top:560px; "> 
            <div class="card-body" 
                style="position:absolute; width:260px; left:90px;  top:-5px; font-size: 110%; color: white;">Lighting Groups
                <div style="position:absolute; width:150px; left:-70px; top:58px;" >   <button v-on:click="clickLightGroup('Group Kit All',true)">          Kitchen All    </button>     </div>
                <div style="position:absolute; width:150px; left:-70px; top:98px;" >   <button v-on:click="clickLightGroup('-',false)">     -   </button>     </div>
                <div style="position:absolute; width:150px; left:-70px; top:138px;" >  <button v-on:click="clickLightGroup('-')">     -   </button>     </div>
                <div style="position:absolute; width:150px; left:-70px; top:178px;" >  <button v-on:click="clickLightGroup('-')">     -   </button>     </div>

                <div style="position:absolute; width:150px; left:75px; top:58px;" >    <button v-on:click="clickLightGroup('-')">  -      </button>     </div>
                <div style="position:absolute; width:150px; left:75px; top:98px;" >    <button v-on:click="clickLightGroup('-')">  -      </button>     </div>
                <div style="position:absolute; width:150px; left:75px; top:138px;" >   <button v-on:click="clickLightGroup('-')">  -      </button>     </div>
                <div style="position:absolute; width:150px; left:75px; top:178px;" >   <button v-on:click="clickLightGroup('-')">  -      </button>     </div>
            </div> 

            <!-- ****************** USER INPUT - LIGHTING SCENES ****************** -->
            <div class="card-body" 
                style="position:absolute; width:260px; left:75px;  top:220px; font-size: 110%; color: white;">Lighting Scenes
                <div style="position:absolute; width:150px; left:-55px; top:58px;">   <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('TV Low')">       TV Low         </button>     </div>
                <div style="position:absolute; width:150px; left:-55px; top:98px;">   <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -      </button>     </div>
                <div style="position:absolute; width:150px; left:-55px; top:138px;">  <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -      </button>     </div>
                <div style="position:absolute; width:150px; left:-55px; top:178px;">  <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -      </button>     </div>

                <!-- relaxing and party are setup in node-red -->

                <div style="position:absolute; width:150px; left:90px; top:58px;">    <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -        </button>     </div>
                <div style="position:absolute; width:150px; left:90px; top:98px;">    <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -        </button>     </div>
                <div style="position:absolute; width:150px; left:90px; top:138px;">   <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -        </button>     </div>
                <div style="position:absolute; width:150px; left:90px; top:178px;">   <button :style="{color: lighting_disable_scenes? 'grey' : ''}"  :disabled="lighting_disable_scenes" v-on:click="clickLightScene('-')">    -        </button>     </div>
            </div> 
        </div> 
    </template>




        
    <!-- ****************** USER INTERFACE - LIGHTING CONTROL ****************** -->
    <!-- ****************** USER INTERFACE - LIGHTING CONTROL ****************** -->
    <template id = "lighting control" >
        <div class="input-card"    style="position:absolute; width:310px; height:490px; left:650px;  top:560px;"> 
            <div class="card-body" style="position:absolute; width:260px; left:75px; top:-5px; font-size: 110%; color: white;"> Lighting Control </div>

            <div          style="position:absolute; width:250px; left:25px; top:50px; "><label>Light:</label></div>
            <div          style="position:absolute; width:250px; left:25px; top:83px;"><label>Brightness:</label></div>
            <div          style="position:absolute; width:250px; left:73px; top:50px; font-size: 100%; color: white;"><label id="circuit_name">{{ curr_input_circuit }}</label></div>
            <div          style="position:absolute; width:250px; left:143px; top:83px; font-size: 100%; color: white;"><label>{{ input_brightness }}</label></div>
            <b-form-input style="position:absolute; width:250px; left:24px; top:120px;" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" lazy v-on:change="sliderChangeBrightness(input_brightness)" id="range-10" v-model="input_brightness" type="range" min="0" max="100"></b-form-input>       <!-- slider brightness input-->
            <!-- ****************** USER INTERFACE - SLIDER ****************** -->

            <!-- ****************** USER INTERFACE - BRIGHTNESS BUTTONS ****************** -->
            <div style="font-size:90% !important;">
              <div style="position:absolute; width:60px; left:5px;  top:160px;" >    <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('0')">Off</button></div>
              <div style="position:absolute; width:60px; left:50px;  top:160px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('5')">5</button></div>
              <div style="position:absolute; width:60px; left:80px; top:160px;" >    <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('10')">10</button></div>
              <div style="position:absolute; width:60px; left:120px; top:160px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('15')">15</button></div>
              <div style="position:absolute; width:60px; left:160px; top:160px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('20')">20</button></div>
              <div style="position:absolute; width:60px; left:200px; top:160px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('25')">25</button></div>
              <div style="position:absolute; width:60px; left:240px; top:160px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('30')">30</button></div>

              <div style="position:absolute; width:60px; left:5px;  top:197px;" >    <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('40')">40</button></div>
              <div style="position:absolute; width:60px; left:45px;  top:197px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('50')">50</button></div>
              <div style="position:absolute; width:60px; left:80px; top:197px;" >    <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('60')">60</button></div>
              <div style="position:absolute; width:60px; left:120px; top:197px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('70')">70</button></div>
              <div style="position:absolute; width:60px; left:160px; top:197px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('80')">80</button></div>
              <div style="position:absolute; width:60px; left:200px; top:197px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('90')">90</button></div>
              <div style="position:absolute; width:60px; left:240px; top:197px;" >   <button class="button_brightness" :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons" v-on:click="sliderChangeBrightness('99')">99</button></div>
            </div>

            <transition name="fade">  
              <div v-if="colour_picker_hide" id="hide" style="position:absolute; width:150px; left:19px; top:250px;"> 
                <color-picker :width="200" :height="200" :disabled="false" startColor="#ff0000" v-model="color" ></color-picker> 
                <div style="position:absolute; width:50px; left:218px; top:-8px;">Submit</div>
                <div style="position:absolute; width:150px; left:227px; top:20px;"><div class="selected-color-info" aria-hidden="false" focusable="true" v-on:click="colourChange_colourWheel"> <svg height="32" width="32"> <circle cx="16" cy="16" r="15" :fill="color" /> </svg> </div></div> 
                <div v-if="colour_picker_hide" id="hide" style="position:absolute; width:85px; left:205px; top:175px;"><button :style="{color: lighting_disable_slider_buttons? 'grey' : ''}"  :disabled="lighting_disable_slider_buttons"  v-on:click="colourChange('warm')">Warm White</button></div>
              </div>  
            </transition>

        </div> 
    </template>

    </b-container>

</template>


























<script> 

import AnimatedNumber from "animated-number-vue";
import ColorPicker from "vue-color-picker-wheel";

export default {
  name: "Floorplan",
  
    components: {
      ColorPicker,
      AnimatedNumber,
    },
   

    data() {
      return {

        colour_picker_hide: false,                    //hide/show all elements within the colour picker card

        curr_input_circuit:"",                        // this is the current user selected circuit
        input_brightness:"",                          // this is the current circuit selected brightness
        color:'#000000',                              // this is the current circuit selected colour (if applicable)
    
        lighting_groups_table: [],                    //used to store the lighting group definitions passed from the lighting groups table 

        lighting_disable_scenes: false,               //disable inputs for set time to allow home automation to process the requestg
        lighting_disable_slider_buttons: false,       //disable inputs for set time to allow home automation to process the requestg
        lighting_disable_timer_single: 1500,
        lighting_disable_timer_group: 3500,
        colourChange_colourWheel_current_time: 0,     //stores the os.time to allow a freeze on colour changes 
        duration: 1000,                               //animated-number animation duration in miliseconds

        light_table: [
            {hc2name:"Garden/BBQ Wall Lights",      brightness_value:"0",   rgbw:false,  brightness_hide:true, colour_value: null},
            {hc2name:"Garden/Garden Bench Lights",  brightness_value:"0",   rgbw:true,   brightness_hide:true, colour_value:"0",      hc2_colour:"0"},
            ],

      


      };

    }, // --- End of data --- //

































    methods: {


    //**************************** SONOS METHODS *********************//
    formatToValue(value) {
      return `${ Number(value).toFixed(0)}`;
    },



    // -- Called if a LIGHT BULB is clicked - sets variables for lighting control panel to update
    clickLight: function(light_name) {
        //Retrieve object for the light bulb
        var light_lookup = this.light_lookup_hc2name(light_name);
        if (light_lookup.colour_value !== null) {this.color = light_lookup.colour_value};

        //Grabbing the brightness and colour of the selected light to display in the lighting control section
        var bright_adjust        = light_lookup.brightness_value;                                               
        if (bright_adjust       == ""){bright_adjust = "0"};
        this.input_brightness    = bright_adjust;
        
        if (light_lookup.rgbw === true) 
            {
            this.input_colour       = light_lookup.colour_value;                                                
            this.colour_picker_hide = true;
            }
        else    
            {this.colour_picker_hide = false;}

        this.curr_input_circuit      = light_lookup.hc2name    //update with single circuit name
    },



    // -- Called if a LIGHTING GROUP button is clicked - sets the light in the lighting controller
    clickLightGroup: function(group_name,colour) {
      this.curr_input_circuit   = group_name                        //update with group circuit name
      this.colour_picker_hide   = colour 
  },




    // -- Called if a LIGHTING SCENE button is clicked - send scene to NR to process and send to HC2
    clickLightScene: function(group_name) {
        this.curr_input_circuit= "Group " + group_name;
            {
            uibuilder.send({
            'topic':            group_name,
            'payload':          "Scene",
            'page':             "xFloorplan",
            })

            //disable the pressed button for set time whilst request is processed
            this.lighting_disable_scenes = true
            setTimeout(() => {
              this.lighting_disable_scenes = false
            }, this.lighting_disable_timer_group)
            }
    },
    





    //this is for the warm white submit button 
    colourChange: function(color) {
    // Send COLOUR to Node Red //
    uibuilder.send({             
        'topic':    this.curr_input_circuit,
        'payload':  color,
        'colour':   color,
        'type':     'colour',
        'page':     "xFloorplan",
    });

    //TIMER to lock user input
    //if group of lights selected, use longer timer
    var curcuit_prefix    = this.curr_input_circuit
    curcuit_prefix        = curcuit_prefix.substring(0, 5);
    var timer = curcuit_prefix == "Group"? this.lighting_disable_timer_group : this.lighting_disable_timer_single

    //disable the pressed button for set time whilst request is processed
    this.lighting_disable_slider_buttons = true
    setTimeout(() => {
      this.lighting_disable_slider_buttons = false
    }, timer);

    }, // -- End of  -- //




    //this is for only the colour wheool submit button (circle)
    colourChange_colourWheel: function() {
    // Send COLOUR to Node Red //

    //TIMER to lock user input
    //if group of lights selected, use longer timer
    var curcuit_prefix    = this.curr_input_circuit
    curcuit_prefix        = curcuit_prefix.substring(0, 5)
    var timer = curcuit_prefix == "Group"? this.lighting_disable_timer_group : this.lighting_disable_timer_single

    var current_time = new Date()
    if ((current_time - this.colourChange_colourWheel_current_time) > timer)        //if enought time has passed allow updates, else do nothing
      {
      uibuilder.send({             
          'topic':    this.curr_input_circuit,
          'payload':  this.color,
          'colour':   this.color,
          'type':     'colour',
          'page':     "xFloorplan",
      })
      //disable the pressed button for set time whilst request is processed
      this.lighting_disable_slider_buttons = true
      setTimeout(() => {
        this.lighting_disable_slider_buttons = false
      }, timer);
      //reset time
      this.colourChange_colourWheel_current_time = current_time
      }

}, // -- End of  -- //






    // Called if slider value has been changed
    sliderChangeBrightness: function(input_brightness)  {
    // Send Updated BRIGHTNESS to Node Red //
    uibuilder.send({
        'topic': this.curr_input_circuit,
        'payload': Number(input_brightness),
        'brightness': Number(input_brightness),
        'page':             "xFloorplan",
    });

    //if group of lights selected, use longer timer
    var curcuit_prefix    = this.curr_input_circuit
    curcuit_prefix        = curcuit_prefix.substring(0, 5);
    var timer = curcuit_prefix == "Group"? this.lighting_disable_timer_group : this.lighting_disable_timer_single

    //disable the pressed button for set time whilst request is processed
    this.lighting_disable_slider_buttons = true
    setTimeout(() => {
      this.lighting_disable_slider_buttons = false
    }, timer);
    
    }, // -- End of  -- //



    //Lookup light data - hc2 name - returns the entire object for the light
    light_lookup_hc2name: function(hc2_name) {
        return this.light_table.find(lights => lights.hc2name == hc2_name); // returns whole object found
      },




    //Refresh entire floorplan page
    reloadPage(){
    window.location.reload()
      },
    


    }, // --- End of methods --- //





























    // Start-up
    mounted() {

          
        /** **REQUIRED** Start uibuilder comms with Node-RED */
        uibuilder.start('/home', '/uibuilder/vendor/socket.io')

        // msg is updated when a standard msg is received from Node-RED
        uibuilder.onChange('msg', (msg) => {
        if (msg.page == "xFloorplan" && this.$route.path == "/xFloorplan") {                            //only run code if correct message type has been received

          if (msg.fp_light_table        != undefined)  {this.light_table         = msg.fp_light_table}

        }});

    }, // --- End of mounted hook --- //

}// -- End of Export -- //

</script>

























<style>
:root{
  
  /* ***************** FLOORPLAN  ***************** */
    --popover-background-colour: #fff;

  /* ***************** DEFAULT SPOT LIGHT COLOURS  ***************** */
  --led-on-colour: orange;
  --led-off-colour: #636363;

}
 
</style>





<style lang="scss" scoped>

[v-cloak]::before { content: "loading…" }


@import url(https://fonts.googleapis.com/css?family=Barlow);



#color-wheel {
  margin-left: auto;
  margin-right: auto;
}



 


/**************** INTERACTIVE LIGHTS *******************/
/* BUTTONS HIDDEN BEHIND LIGHTS ON FLOOR PLAN */
.btn-primary-outline {
  background-color: transparent !important;
  border-color: transparent !important;
  box-shadow: 0 0 0 0 #1c1c1c !important;
}
.btn:focus {
  outline: none;
  box-shadow: none;
}

.button_brightness {
  background-color: transparent !important;
  border-color: transparent !important;
  box-shadow: 0 0 0 0 #1c1c1c !important;
}

/* LIGHT BRIGHTNESS VALUE NEXT TO LIGHT BULB */
.status[animated-number="0"] {
  font-size: 220% !important; 
  display:none;
}

.light_brightness {
  font-size: 90% !important; 
  color: #383737;
}




/**************** LIGHTING *******************/
.fa-window-minimize{
  transform: scale(1.1,1); 
}





/**************** LIGHTING CIRCUIT DESCRIPTION POPUP WINDOW *******************/
/* POP-UP BOX FOR LIGHTS ON FLOOR PLAN - f0f0f0*/
.popover {
  border: 2px transparent;
  background-color: var(--popover-background-colour);
  font-size: 12px;
}
.popover .arrow {
  display: none;
}




/*****************ALL THE INPUT CARDS BELOW THE FLOOR PLAN*****/
.input-card{
  background-color: var(--card-background-colour);
  box-shadow: 0 5px 12px 0 var(--box-shadow);
  border-radius:.15rem!important;
}



</style>