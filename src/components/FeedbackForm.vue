<template>
       <div class="container"  v-if="!value">
       <div class="box-container" >
         <div> <img width="120" src="https://referthru.com/Assets/Logo.png" /></div>
         <div class="tittle" style="margin:.5em .5em;font-size:18px">StayWell Spa Service Hinjewadi, Pune</div>
          <br />
        <form action="" id="referform" @submit.prevent="signup">
          <label class="field-label tittle_second"
            >How do you rate this business?</label
          >
          <br />

          <div class="form-field">
          <div v-for="index in 5" :key="index" class="star-container"
            @click="setRating(index)" @mouseover="hoverRating = index" @mouseleave="hoverRating = rating">
            <div class="star-wrapper">
              <i :class="{ 'fa-solid fa-star': true, 'selected': index <=this.rating, 'hovered': index <= this.hoverRating }"></i>
            </div>
          </div>
        </div>


          <label for="rate" class="business-fefer"
            >Will you refer this business to your family and friends?</label
          >
          <fieldset style="padding:.3em 0px;border:none;margin-top:.3em">
            <div class="some-class" id="radio">
              <input
                type="radio"
                class="radio"
                value="true"
                id="yes"
                v-model="check"
                 @change="handleInput()"
              />
              <label for="yes" class="field-label" >Yes</label>
              <input
                type="radio"
                class="radio"
                value="false"
                id="no"
                v-model="check"
                @change="handleInput()"
              />
              <label for="no" class="field-label">No</label>
            </div>
          </fieldset>
          <p class="field-label" style="margin-bottom:0.3em;">   
            Enter below for a chance <br />to win ₹ 1000
          </p>
          <div class="form">
            <div class="block_form"> 
              <label for="name" class="field-label name_align">Your Name</label>
              <input
                class="w-input"
                name="name"
                id="name" 
                type="text"
                placeholder="Your Name"
                style="padding-left:0.4em;position:relative;left:7%;width:60%"
                minlength="3"
                 @input="handleInput()"
                onkeypress="return (event.charCode > 64 && event.charCode < 91) || (event.charCode > 96 && event.charCode < 123)"
                v-model="name"
                required
               
              />
            </div>
        <div  style="position: relative" class="block_form">
        <label for="phone" style="position:relative;top:.3em;left:.3em">Your Phone</label>
       <div style="display: flex; position: relative; left: 36.8%; top: -0.9em;" id="phoness">
        <div style="border: .18em solid orangered; border-right: 0px; padding:11px; padding-right: 0px; font-size: 0.75em;" class="div1">+91</div>
        <input 
        style="border-left: 0px;" 
        name="phone" 
        id="phone" 
        type="text" 
        placeholder="Your Phone"  
        @keypress="AllowOnlyNumbers()"
        @input="handleInput()"
        maxlength="10" 
        minlength="10" 
        v-model="phone"
        required />
       </div>
            </div>
            <button
              class="submit-button "
              id="submit-button"
              type="submit"
              :disabled="isDisabled"

            >
              Submit
            </button>
          </div>
        </form>
          
       </div>
       
       </div>
       <div v-if="value&&afterSubmition" id="afterSubmittion"><img src='@/assets/success icon.png' width='90px' hieght='100px' > <br/><p>Thank You for your feedback. </p></div>
</template>
<script>
export default{
    data(){
        return{
            rating: 0,
      hoverRating: 0,
      name:"",
      phone:"",
      check:null,
      value:false,
      isDisabled:true,
      afterSubmition:true
        }
    },
    methods: {
    setRating(rating) {
      this.rating = rating;
      this.handleInput();
      console.log(this.rating)
      console.log(this.hoverRating)
       },
    signup() {
    //    axios.post("http://www.shanmukh.localhost/:id").then(Response => 
    //    this.getData(Response.data))
    //   console.log('Form submitted with rating:', this.rating);
    // },
    // getData(data){
    //   if(true){

    //   }
   
      this.value=true 
      
      setTimeout(()=>{
        window.location='https://app.referthru.com/#/login'
        this.afterSubmition=false
        
      },3000)
    
    },
    // checking(){
    //   if(this.name!==""&&this.phone!==""&&this.check&&this.rating!==0){
    //     this.isDisable=false
    //   }
    // },
    AllowOnlyNumbers(){
       this.phone = this.phone.replace(/[^0-9]/g,"")
    },
     handleSubmittion(){
      console.log(this.check);
      this.handleInput()
     },
      handleInput(){
         if(this.name.trim()!=="" && this.phone.length===10 && this.check !==null && this.rating!==0){
              this.isDisabled=false
            }
  },
    }

}
</script>
<style scoped>
.container{
    border: 2px solid orangered;
    padding: 30px 20px;
    max-width: 392px;
    position: absolute;
    overflow: hidden;
    left: 34%;
    border-radius: 60px;
}

  .star-container {
  display: inline-block;
  margin:25px 0px;
}
.star-container .star-wrapper {
  width: 40px;
  height: 40px;
  font-size: 27px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.form-field i.selected,
.form-field i:hover {
  color: gold;
  
}

.form-field i.hovered{
  color: gold; 
}
i{
    color:wheat;
    font-size: 30px;
}
#phone,#name{
  border: 2px solid orangered;
  position: relative;
  right: 0px;
  padding:10px 4px;
  width:50%;
  outline:0px;
  font-size: 13px;
  font-weight: normal;
  
  
}
/* #phone:hover,#name:hover,.div1:hover{
  border-color: blue;
} */
#yes,#no{
  width: 25px;
  height: 25px;
  margin-bottom: 10px;
  
  
}
/* .div1{
width: 35px;

} */
.field-label{
  margin: 8px ;
  position: relative;
  top: -5px;
}
.submit-button{
  position: relative;
  left: 40%;
  padding: 6px 6px;
  background-color: orangered;
  color:whitesmoke;
  border: none;
  font-size: 20px;
  
}
.submit-button:disabled{
  opacity: .6;
}
#afterSubmittion{
 width: 300px;
 position: absolute;
 left: 40%;
 top: 40%;
 transform: translateY(-50%);

}
#afterSubmittion img{
  position: relative;
  left: 70px;
}
  @media  screen and (max-width: 512px) {
    
  .container {
    max-width: 100%;
    left: 0;
    padding:20px 15px;
    margin: 0 auto;
  }

  .star-container {
    margin: 15px 0;
  }
.div1{
  position: relative;
  
}
  #phone, #name {
    width: 52%;
  }
 #phone{
  width: 49%;
 }
 
 
 #phoness{
 position:relative;
  left:20%;
 }
  .submit-button {
    left: 50%;
    transform: translateX(-50%);
  }

  #afterSubmittion {
  
    left: 50%;
    transform: translate(-50%, -50%);
  }

  #afterSubmittion img {
   position: relative;

    left: 50%;
    transform: translateX(-50%);
  }
  #afterSubmittion p{
    position: relative;
    left:60%;
    transform: translateX(-50%);
  }

  .tittle{
    font-size:2px;
    
  }
} 
 @media screen and (width: 540px){
  .container{
    max-width: 70%;
    position: absolute;
    padding: 30px 11px;
    left: 12%;
  }
  #phone{
    width: 50%;
  }
   
 }
 @media screen and(width: 768px) {
  .container{
    max-width: 100%;
  }
 }
 @media screen and (width:375px){
  .container{
    max-width: 100%;
    margin: 0 auto;
    padding: 30px 10px;
    
  }
  #phone{
    width:49.5%;
    padding:10px 0px;
    position: relative;
   
  }
  .div1{
    position: relative;
    width: 36px;
    
  }
 }
 @media screen and (width:414px){
  .container{
    max-width:100%;
    padding: 30px 20px;
  }
  .div1{
    position: relative;
    left: -1.5%;
    width:32px;
  }
  #phone{
    position: relative;
    left: -1.5%;
    width:51%;
  }
 }
 @media  screen and (width:390px) {
  .container{
    width: 100%;
  }
   .div1{
    position:relative;
    left:-2px;
   
   }
   #phone{
    position:relative;
    left: -2.5px;
     width: 50.5%;
   }
 }
 @media screen and (width:430px){
  .container{
    position: inherit;
    left:10%;
    padding:30px 20px;
    width: 92%;
  }
  #phone{
    width: 50%;
  }
 }
 @media screen and (width: 412px){
  .container{
    position: inherit;
    left:10%;
    padding:30px 20px;
    width: 95.5%;
  }
  #phone{
    width: 50%;
  }
 }
@media screen and (width:360px){

  .container{
    width: 100%;
    padding: 10px;
  }
  #phone{
    position: relative;
    width: 51%;
  }
  .div1{
    position: relative;
    left: 1%;
    
  }
}
@media screen and (max-width:280px){
  .container{
    width:100%;
    padding:30px 2px;
  }
  #phone,#name{
    max-width: 50%;
  }
  #phone{
    width:37%;
    position: relative;
    left: 25px;
  }
.div1{
  position: relative;
  left: 25px;
}
.tittle{
  font-size: 1vw;
}
}
@media screen and (width:512px){
  .container{
    width:75%;
    position:absolute;
    left:13%;
  }
  #phone{
    width: 50%;
  }
}
</style>
