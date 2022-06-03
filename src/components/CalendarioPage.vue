<template>
    <body>
    <header>
      <nav>
        <div class="nav">
          <div class="imgContainer">
            <img src="../assets/logo2.png" alt="logo" />
          </div>
          <div id="menu">
            <ul>
              <li><a href="" @click="goperfil()">Perfil</a></li>
              <li><a href="" @click="goeventos()">Eventos</a></li>
              <li><a href="" @click="goamigos()">Amigos</a></li>
            </ul>
          </div>
        </div>
      </nav>
    </header>
    <main>
    <article>
      <h1 class="title">Calendario</h1>
    </article>
    <article>
      <ul v-for="(item,index) in eventosInfo" :key="item.id">
        <div class="eventosMostrados">
          Evento:  {{index+1}} : {{item.name}}  || Start: {{item.eventStart_date}}  || Location: {{item.location}}
        </div>
      </ul>
    </article>
  </main>
  </body>
</template>

<script>
export default {
     name: 'HomePage',
       data(){
    return{
      eventosInfo : []
    }
  },

  async mounted(){
    const token = localStorage.getItem('token');
    const id = localStorage.getItem('id');
    const api = 'http://puigmal.salle.url.edu/api/v2/users/'+id+'/events/future';
    await this.axios.get(api, {headers: {"Authorization" : `Bearer ${token}`}}).
    then(res => {
      this.eventosInfo = res.data
    })
  },

  methods:{
    
    goperfil(){
      this.$router.push('/perfil'); 
    },
    goeventos(){
      this.$router.push('/eventos'); 
    },
    goamigos(){
      this.$router.push('/amigos'); 
    }
    }
}
</script>

<style>
.nav {
  display: flex;
  flex-direction: row;
  align-items: center;
  flex-wrap: wrap;
  background-color: #c1272d;
  height: 100px;
}
.imgContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  height: 100px;
}

.nav div img {
  margin-left: 20px;
  width: 75px;
}

#menu ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.eventosMostrados{
margin-bottom: 25px;
margin-left: 20px;
}

#menu ul a {
  color: white;
  text-decoration: none;
  font-size: 12pt;
  padding-left: 50px;
  font-family: Verdana;
  letter-spacing: 1px;
}
#menu ul li :hover {
  text-decoration: underline;
}

.title {
  margin-left: 20px;
  padding-top: 35px;
  padding-bottom: 35px;
  text-decoration: underline;
  font-family: Verdana;
  font-size: 25pt;
  font-weight: bold;
  color: #c1272d;
}

article form {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;

  margin-left: 20px;
  width: 275px;
  gap: 10px;
}
.textareaForm {
  font-family: Verdana;
  border: 2px solid #c1272d;
  margin-top: 10px;
  width: 275px;
}

input[type="submit"] {
  width: 150px;
  background-color: #c1272d;
  border: none;
  color: white;
  padding: 10px 30px;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  font-family: Verdana;
  font-size: 9pt;
  margin-top: 10px;
}
input[type="text"] {
  font-family: Verdana;
  border: 2px solid #c1272d;
}
input[type="date"] {
  border: 2px solid #c1272d;
}

@media (max-width: 375px) {
  .nav div img {
    display: flex;
    flex-wrap: wrap;
    width: 75px;
  }
  .nav div a {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    padding-bottom: 5px;
  }
  #menu ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  #menu ul a {
    color: white;
    text-decoration: none;
    font-size: 12pt;
    padding-left: 20px;
    font-family: Verdana;
    letter-spacing: 1px;
  }
  #menu ul li :hover {
    text-decoration: underline;
  }

  .title {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    padding-top: 35px;
    padding-bottom: 35px;
    text-decoration: underline;
    font-family: Verdana;
    font-size: 25pt;
    font-weight: bold;
    color: #c1272d;
    margin-right: 20px;
  }
  article form {
    margin-left: 45px;
  }
}
</style>