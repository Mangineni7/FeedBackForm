<template>
  <div class="container-fluid" v-if="!value">
      <form  class="mx-auto pt-0" @submit.prevent="signup">
       <div style="width:100px;height:100px"> <img src="https://referthru.com/Assets/Logo.png" class="img-fluid mt-5"></div>
       <p style="font-size:18px;">StayWell Spa Service Hinjewadi, Pune</p>

       <p>How do you rate this business?</p>

       <div class="d-flex flex-row ">
       <div  class="me-2 mb-3" v-for="index in 5" :key="index" @mouseover="hoverRating=index" @mouseleave="hoverRating=rating"
       @click="starRating(index)">
        <i :class="[{'fa-solid fa-star':true,'selected':index<=this.rating, 'hovered':index<=this.hoverRating}]"></i>
       </div>
       </div>

       <label class="form-label">Will you refer this business to your family and friends?</label>
       <fieldset class="d-flex flex-row mb-1">
        <div class="form-check me-2">
         <input class="form-check-input fs-5 " type="radio" name="flexRadioDefault" value="true" v-model="check" id="flexRadioDefault1"
         @change="disablechoice()">
            <label class="form-check-label mt-1 me-1" for="flexRadioDefault1">
            Yes
           </label>
        </div>
        <div class="form-check">
        <input class="form-check-input fs-5 " type="radio" name="flexRadioDefault" value="false" v-model="check" id="flexRadioDefault2"
        @change="disablechoice()" >
       <label class="form-check-label  mt-1" for="flexRadioDefault2">
         No
       </label>
       </div>

       </fieldset>
       <p>Enter below for a chance <br>to win ₹ 1000</p>
     
        <div class="mb-1 row">
    <label for="staticEmail" class=" col-6 col-sm-5 col-form-label label ">Your Name</label>
    <div class=" col-6 col-sm-7 ">
      <input type="text"  class="form-control " id="staticEmail" 
       v-model="name"
      onkeypress="return (event.charCode > 64 && event.charCode < 91) || (event.charCode > 96 && event.charCode < 123)"
      @input="disablechoice()">
    </div>
  </div>
  <div class="mb-3 row">
    <label for="inputPassword" class=" col-6 col-sm-5 col-form-label label ">Your Phone</label>
    <div class=" col-6 col-sm-7   code">
      <div class="country-code" style="font-weight:normal;font-size:16px">+91</div>
      <input type="tel" class="form-control  phone " id="inputPassword"
      minlength="10"
      maxlength="10"
      v-model="phone"
      @input="AllowNumbers();disablechoice()">
    </div>
  </div>

  <button type="submit" class=" btns " :disabled="isDisabled">Submit</button>
   </form>
  </div>
   <div v-if="value" class="styles"><img src='@/assets/success icon.png' width='90px' hieght='100px'> <br/><p>Thank You for your feedback. </p></div>
</template>
<script>
export default{
  data(){
    return{
      rating:0,
      hoverRating:0,
      name:"",
      phone:'',
      check:null,
      value:false,
      isDisabled:true,
    }
  },
    methods:{
          starRating(star){
            this.rating=star
            console.log("rating :"+this.rating);
            this.disablechoice()
          },
          AllowNumbers(){
             this.phone=this.phone.replace(/[^0-9]/g,'')
          },
          
          signup(){
            this.value=true
            console.log("rating :"+this.rating);
            console.log("checking :"+this.check);
            console.log("name :"+this.name);
            console.log("phone :"+this.phone);
          },
          disablechoice(){
            if(this.name.trim()!=="" && this.phone.length===10 && this.check !==null && this.rating!==0){
              this.isDisabled=false
            }
          }
    }
  
}
</script>
<style scoped>
i.selected,
i:hover{
  color: gold;
}
i.hovered{
  color:gold
}
i{
  color: rgb(194, 170, 139);
  font-size: 28px;
}
form{
  border: 2px solid orangered;
  padding: 30px 20px;
  border-radius: 60px;
  width: 400px;
}
.form-control{
  border: 2px solid orangered;
  font-size: 16px;
  margin-left: -20px;
 
}
.form-control:hover{
  border-color: blue;
}
.country-code{
  position: absolute;
  top: 9px;
  left:5px;
  
 
}
.phone{
  padding-left:40px
}
.code{
  position: relative;
}
.btns{
  background-color: orangered;
  margin-left: 140px;
  border: none;
  padding:5px 8px;
  border-radius: 10px;
  color: white;
}
.btns:disabled{
  opacity: 0.6;
}
.styles{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
 
}
.styles img{
    position:relative;
    left:70px
  }

@media screen and (max-width: 540px){
  .form-control{
    margin-left:-50px;
  }
  .country-code{
   position: absolute;
    left: -25px;
  }
  .styles p{
    font-size: 13px;

  }
  .styles img{
    position:relative;left:40px
  }
  .styles{
    position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  }
  
}
@media screen and (width: 280px) {
  .styles p{
    font-size: 10px;

  }
  .styles img{
    position:relative;
    left:30px;
    width:80px;
    height: 80px;
  }
}

</style>
