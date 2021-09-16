<template>
  <div class="container bg-white">
     
    <div class="row">
      <div class="col d-block m-auto ">

        <form v-show="!closeForm" @submit="enviar" class="p-3 shadow">

          <div class="row mb-md-3">
            <div class="col-md-6">
              <label for="name">Nome </label>
              <input v-model='form.name' id="name" type="text" class="form-control" required>
            </div>
            <div class="col-md-6">
              <label for="sobrenome">Sobrenome </label>
              <input v-model='form.sobrenome' id="sobrenome" type="text" class="form-control" required>
            </div>
            
          </div>

          <div class="row mb-md-3">
            <div class="col-md-6">
              <label for="email">E-mail </label>
              <input v-model="form.email" id="email" type="email" class="form-control" required>
            </div>
            <div class="col-md-6">
              <label for="cargo">Cargo </label>
              <input v-model="form.cargo" id="cargo" type="text" class="form-control"  required>
            </div>
          </div>

          <div class="row mb-md-3">
            <div class="col-md-4">
              <label for="tel1">Telefone </label>
              <input v-model="phone[0]" v-mask="'(##) #########'" id="tel1" type="text" class="form-control"  required>
            </div>
            <div class="col-md-4">
              <label for="tel2">Celular </label>
              <input v-model="phone[1]" v-mask="'(##) #########'" id="tel2" type="text" class="form-control" >
            </div>
            <div class="col-md-4">
              <label for="tel3">Outro </label>
              <input v-model="phone[2]" v-mask="'(##) #########'" id="tel3" type="text" class="form-control" >
            </div>
          </div>

          <div class="row mb-md-3">
            <div class="col-md-6">
              <label for="endereco">Endereço </label>
              <input v-model="form.endereco" id="endereco" type="text" class="form-control"  required>
            </div>
            <div class="col-md-2">
              <label for="number">Número </label>
              <input v-model="form.number" id="number" type="text" class="form-control" required>
            </div>
             <div class="col-md-4">
              <label for="name">Complemento </label>
              <input v-model="form.complemento" id="complemento" type="text" class="form-control" required>
            </div>
          </div>

          <div class="row mb-md-3">
            <div class="col-md-3">
              <label for="cep">CEP </label>
              <input v-model="form.cep" v-mask="'#####-###'" id="cep" type="text" class="form-control"  required>
            </div>
            <div class="col-md-6">
              <label for="city">Cidade </label>
              <input v-model="form.city" id="city" type="text" class="form-control" required>
            </div>
             <div class="col-md-3">
              <label for="uf">Estado </label>
              <input v-model="form.uf" id="uf"  type="text" class="form-control" required>
            </div>
          </div>

          <div class="button">
            <button type="submit" class="btn btn-info d-block m-auto">GERAR</button>
          </div>
          
        </form>

        <div v-show="showAss" class="bg-white">
          <div class="ass d-block m-auto shadow" style="background: #fffff;box-shadow: unset !important;" ref="assinatura">
            <div class="container m-0 p-0">
              <div class="row m-0 p-0">
                <div class="col-4 box-info-1 p-0">
                  <div class="box1">
                    <div class="info1 d-flex">
                    <img src="../assets/img/logo.png" class="img-fluid logo d-block m-auto" alt="Logo">
                  </div>
                  <div class="info2 ">
                    <div class="d-flex justify-content-center">
                      <img src="../assets/logo.png" class="img-fluid m-1 rede" alt="Logo">
                      <img src="../assets/logo.png" class="img-fluid m-1 rede" alt="Logo">
                      <img src="../assets/logo.png" class="img-fluid m-1 rede" alt="Logo">
                      <img src="../assets/logo.png" class="img-fluid m-1 rede" alt="Logo">
                    </div>
                    <h2 class="text-center"><strong>espro</strong>.org.br</h2>
                  </div>
                  </div>
                </div>
                <div class="col-4 box-info-2 p-0">
                  <div class="info2">
                    <h1 class="name pb-1">{{form.name}} {{form.sobrenome}}</h1>
                  <p class="cargo"> <span>{{form.cargo}}</span></p>
                  </div>
                  <div class="d-flex flex-column box-box info1">

                    <div class="d-flex box">
                      <img src="../assets/logo.png" class="img-fluid icon" alt="logo">
                      <p class="m-0">
                         <span v-for="item in form.phone" :key="item" > {{ item }}  </span>
                      </p>
                    </div>

                    <div class="d-flex box">
                      <img src="../assets/logo.png" class="img-fluid icon" alt="logo">
                      <p class="m-0">
                        <span> {{ form.email }} </span>
                      </p>
                    </div>

                    <div class="d-flex box">
                      <img src="../assets/logo.png" class="img-fluid icon" alt="logo">
                      <p class="m-0">
                        <span> {{ form.endereco }}, {{form.number}}, {{form.complemento}} {{form.cep}} - {{ form.city}}/{{form.uf}} </span>
                      </p>
                    </div>
                  </div>
                </div>
                <div class="col-4 box-info-img p-0">
                  <div class="d-flex">
                    <img src="../assets/img/selo.png" class="img-fluid" alt="selo">
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="mt-5 d-flex justity-content-center">
            <button @click="download" class="d-block m-auto btn btn-info">Download</button> 
            <button @click="voltar" class="d-block m-auto btn btn-info">Voltar</button>
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import html2canvas from 'html2canvas';
export default {
  name: 'Form',
  data(){
    return{
      closeForm: true,
      showAss: true,
      form:{
        name: 'Mateus',
        sobrenome: 'Pereira',
        email: 'mateus.pereira@cantacom.com.br',
        cargo: 'Desenvolvedor Web',
        phone: ['(16) 988522361', '(16) 988522362'],
        endereco: 'Rua da Consolação',
        number: '247',
        complemento: '11º andar',
        cep: '01301-903',
        city: 'São Paulo',
        uf: 'SP'
      },
      phone: [],
      phones: [],
    }
  },
  methods: {
    checkPhone(){
      let tem = false
      this.phone[0] || this.phone[1] || this.phone[2] ? tem = true : console.log('não')

      if(tem){
        this.phone.map( result => {
          if(result){
            this.form.phone.push(result)
            this.phones.push(result)
          }
        })
      }
    },
    enviar(event){
      event.preventDefault()
      this.checkPhone()
      console.log(this.form)
      this.closeForm = true
      this.showAss = true
    },
    async download(){

      const el = this.$refs.assinatura;

      const options = {
        type: "dataURL",
      };
      
      const printCanvas = await html2canvas(el, options);

      const link = document.createElement("a");
      link.setAttribute("download", "assinatura.png");
      link.setAttribute(
        "href",
        printCanvas
          .toDataURL("image/png")
          .replace("image/png", "image/octet-stream")
      );
      link.click();
    },
    voltar(){
      this.closeForm = false
      this.showAss = false
    }
  }
}
</script>

<style scoped lang="scss">
form{
  border-radius: 15px;
  label{
    position: relative;
    left: 10px;
  }
  .form-control{
    border: none;
    border-radius: 0px 0px 5px 0px;
    border-bottom: 1px solid black;
    margin: 5px 0 10px 0;
    transition: 1s;
  }
  .form-control:focus{
    border: none;
    border-radius: 0px;
    border-bottom: 1px solid #185b90;
    box-shadow: none;
  }
  .form-control:hover{
    border-bottom: 1px solid #185b90;
  }
  
}
.button{
  height: 40px;
}
button{
  background: #185b90;
  color: white;
  font-weight: 500;
  letter-spacing: 0.5px;
  border: none;
  border-radius: 20px;
  transition: 1s;
}
button:hover{
  position: relative;
  color: white;
  top: -2px;
}

.ass{
  border: 1px solid black;
  min-width: 732px;
  max-width: 732px;
  min-height: 230px;
  max-height: 230px;
  padding: 10px 0;
  background: #fff;
  .row{
    min-width: 730px;
    max-width: 730px;
    min-height: 210px;
    max-height: 210px;
  }
  .box1{
    border-right: 2px solid #185b90 ;
    margin-right: 30px;
  }
  .name{
    font-size: 25px;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin: 10px 0 4px;
  }
  .cargo{
    font-size: 16px;
    span{
      background: #185b90;
      color: white;
      padding: 5px 13px;
      border-radius: 20px;
      text-transform: uppercase;
      letter-spacing: 1px;
    }
  }
  .box-box{
    width: 280px;
    .box{
      height: 35px;
      margin-bottom: 1px;
      .icon{
        height: 20px;
        width: 20px;
        margin: 5px 8px 0 0;
      }
      p{
        line-height: 18px;
        
        span{
          font-size: 14px;
          letter-spacing: 0.3px;
        }
      }

    }
  }
  
  
  .box-info-1, .box-info-2{
    height: 210px;
    max-width: 300px;
    min-width: 300px;
    .info1{
      height: 130px;
    }
    .info2{
      height: 80px;
    }
    .logo{
      width: 80%;
    }
    .rede{
       height: 20px;
       padding: 0 0.5px;
    }
    h2{
      font-size: 23px;
      color: #185b90;
    }
  }
  .box-info-2{
    max-width: 300px;
    min-width: 300px;
  }
  .box-info-img{
    width: 130px;
    div{
      height: 100%;
      img{
        height: 190px;
        display: block;
        margin: auto auto auto 0px;
      }
    }
  }
}

</style>
