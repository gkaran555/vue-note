<template>
  <div class="dropdown" :class="{open: is_open}">
    <el-badge  :value="notification.length" class="item" >
        <el-button size="small" @click.prevent="toggleOpen"><i class="el-icon-bell"></i></el-button>
    </el-badge>
    
      <transition-group name="list" tag="ul">
        <li v-for="note in notification" :key="note.id" @click="markAsRead(note)">
          <div class="okolo">
            <img :src="note.image" alt="">
            <a :href="note.link"
                target="_blank"
                v-text="note.title"
                ></a>
          </div>  
        </li>
       </transition-group> 
     
    
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',

  methods: {
     markAsRead: function(note) {
      //  alert(note.title);
      const noteIndex = this.notification.indexOf(note);
      this.notification.splice(noteIndex, 1);
      },
      toggleOpen(){
        this.is_open = !this.is_open;

        // var time = this.notification.expires;
        // setTimeout(this.markAsRead, time); 
      }
        
  },
  data(){
    return {
      is_open: false,
      notification: [
          {
            id: 1321,
            type: 'text',
            title: 'Test notification',
            text: 'Test text notification',
            expires: 3600
          },
          {
            id: 4322,
            type: 'bonus',
            title: 'You win a bonus!',
            requirement: 'Deposit $50 to win',
            expires: 3600
          },
          {
            id: 5453,
            type: 'Promotion',
            image: 'http://www.absolat.com/images/promotion-in-marketing.jpg',
            title: '%30 off on sports betting',
            link: 'https://www.google.com/',
          },
          {
            id: 5236,
            type: 'text',
            title: 'Test notification',
            text: 'Test text notification',
            expires: 5
          }
        
        ]
      }
     }
  } 
</script>


<style scoped lang="scss">
.item {
  margin-bottom: 20px;
}
.dropdown{
  max-width: 200px;
}
ul {
  background: white;
  width: 100%;
  display: none;
  border-top: 30px #009fff solid;
  list-style-type: none;
  margin: 0;
  padding: 0;
  box-shadow: 0 5px 20px 0 rgba(0,0,0, .25);
  box-sizing: border-box;
  transition: all .3s ease;
  position: relative;
  .okolo {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
  }
  li:hover{
    background: #e6f2f2;
    cursor: pointer;
  }
  img {
    border-radius: 50%;
    width: 30%;
  }
  li{
  display: block;
  padding: 15px 15px;
  width: 100%;
  box-sizing: border-box;
  }
 
}

ul:after, ul:before {
	bottom: 100%;
	left: 50%;
	border: solid transparent;
	content: " ";
	height: 0;
	width: 0;
	position: absolute;
	pointer-events: none;
}

ul:after {
	border-color: rgba(136, 183, 213, 0);
	border-bottom-color: #009fff;
	border-width: 40px;
	margin-left: -40px;
}
ul:before {
	border-color: rgba(194, 225, 245, 0);
	border-bottom-color: #009fff;
	border-width: 46px;
	margin-left: -46px;
}

.dropdown.open ul{
  display: block;
  
}

.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

</style>
