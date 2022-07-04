<template>
  <div class="fon">
    <div class="menu">
      <div class="logo"></div>
      <div class="inform"><marquee behavior="scroll" direction="left" >Добро пожаловать на сайт </marquee></div>
    <div class="menuu"><RouterLink to="/">Home</RouterLink> <p style="color:#2c5592">|</p>
    <RouterLink to="/products">Products</RouterLink> <p style="color:#2c5592">|</p> 
    <RouterLink to="/login">Login</RouterLink> <p style="color:#2c5592">|</p> 
    <RouterLink to="/cart">Cart</RouterLink>
    </div></div>
    <RouterView />

  </div>
</template>

<script>
import { createClient, provideClient } from '@urql/vue';
export default {
  setup() {
    const client = createClient({
      url: "http://38.242.229.113:8055/graphql",
      fetchOptions: () => {
      
      const token = localStorage.getItem('token')
      return {
        headers: { authorization: token ? `Bearer ${token}` : '' }
      };
    },
    });
    
    provideClient(client);
  }
}
</script>

<style scoped>
.logo{background-image: url("https://cdn.worldvectorlogo.com/logos/apple-4.svg");
width: 55px;
background-size: cover;
 border: 3px solid #53da3f;

}
.fon{background-image: url("https://img.freepik.com/free-photo/blue-sky-with-clouds_1127-282.jpg");
background-size: cover;
width: 100%;
background-attachment:fixed;
}
.inform{ width: 50%;
background-color: #e8e8e6;
}
.menu{ 
    
    height: 75px;
    display: flex;
    align-items: center;
    justify-content: space-around;
        border-bottom: 1px solid;
    box-shadow: rgb(44 85 146) 0px 19px 38px -29px inset; 
}
.menu h1{ 
      font-weight: initial;
      font-size: unset;
}
.menuu{ 
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
a{
text-decoration: none;
color: #000000;
padding: 0px 10px 0px 10px;
font-size: unset;
text-transform: uppercase;
font-weight: bold;
}
.pro {
color: black;
     color: #646f81; 
     text-shadow: 7px -4px 3px #646f81, 0 0 0em #657081; 
     text-decoration: line-through; 
    }
    .sto{
     color: #e8e8e6; 
color: black;
     text-shadow: 7px -4px 3px #68748a, 0 0 0em #646f81; 
}
 .header
{background-color: #f6f6f6;} 
.logo{
display: flex;
    justify-content: center;
    font-size: 350%;
    align-items: center;
    margin: 1%;
    height: 10px;
}
.logo{
     display: flex; 
     justify-content: flex-start; 
     font-size: 350%; 
     align-items: center; 
     margin: 1%; 
     padding-left: 1%; 
     color: white;
    background-color: black; 
     height: 62px; 
  text-shadow: 7px -4px 5px #e7dec4, 0 0 5em #e7dec4;
    }

</style>