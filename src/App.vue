 <template>
  <div id="app">
    <div id="main-wrapper">
      <!-- Menu -->
      <div :class=" scrollY>98 ? '_1menu _1menu_fixed': '_1menu'">
        <div class="container-fluid">
          <div class="row align-items-center">
            <div class="col-12 col-md col-lg">
              <div class="_1menu_resume">
                <a href="/static/img/myCv.pdf" download="download">
                  <button class="_2btn _btn_large">
                    <span class="_pre_icon"><Icon type="md-document" /></span>  
                    Download My Resume
                  </button> 
                </a>
              </div>
            </div>

            <div class="col-12 col-md-auto col-lg-auto">
              <ul class="_1menu_list">
                <li>
                  <a href="#one" @click="tab = 1" :class="tab == 1? '_1menu_list_text _active' : '_1menu_list_text'">About</a>
                </li>
                <li>
                  <a href="#two" @click="tab = 2" :class="tab == 2? '_1menu_list_text _active' : '_1menu_list_text'">Services</a>
                </li>
                <li>
                  <a href="#three" @click="tab = 3" :class="tab == 3? '_1menu_list_text _active' : '_1menu_list_text'">Projects</a>
                </li>
                <li>
                  <a href="#four" @click="tab = 4" :class="tab == 4? '_1menu_list_text _active' : '_1menu_list_text'">Contacts</a>
                </li>
              </ul>
            </div>

            <div class="col-12 col-md col-lg">
              <div class="_1menu_right">
                <button class="_1btn _btn_large">
                  Available For New Projects
                  <span class="_suf"><Icon type="ios-return-right" /></span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- Menu -->

      
      <!-- Mobile menu -->
      <div :class=" scrollY>98 ? '_mob_menu _1menu_fixed': '_mob_menu'">
        <div class="_mob_menu_logo">
          <h2>Shipu</h2>
          <!-- <router-link to=""><img class="_mob_menu_logo_img" src="../static/img/logo.png" alt="logo" title="logo"></router-link> -->
        </div>

        <div class="_mob_menu_button">
          <Icon @click="isOpen = true" class="_mob_menu_button_icon" type="md-list-box" />
        </div>
      </div>

      <div :class="isOpen == true? '_mob_menu_nav_open _mob_menu_nav' : '_mob_menu_nav'">
        <ul class="_1menu_list">
          <li>
            <a @click="isOpen = false" href="#one" class="_1menu_list_text _active">About</a>
          </li>
          <li>
            <a @click="isOpen = false" href="#two" class="_1menu_list_text">Services</a>
          </li>
          <li>
            <a @click="isOpen = false" href="#three" class="_1menu_list_text">Projects</a>
          </li>
          <li>
            <a @click="isOpen = false" href="#four" class="_1menu_list_text">Contacts</a>
          </li>
        </ul>

        <p @click="isOpen = false" class="_mob_menu_nav_close"><Icon type="md-close" /></p>
      </div>
      <!-- Mobile menu -->

      <div class="_main_layout">
        <router-view></router-view>
      </div>

      <!-- Footer -->
      <div class="container">
        <div class="_footer">
          <p class="_footer_text">© year 2022. Designed by <span>Minhajul_abeeden</span>. All rights reserved.</p>
        </div>
      </div>
      <!-- Footer -->
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      isOpen:false,
      scrollY: 0,
      tab: 1,
      bottomOfWindow: 0
    }
  },

  methods:{
    // onClickss(){
    //   alert('hi');
    // },

    handleScroll(){
      this.scrollY = window.scrollY
    }
  },
  
  created() {
   
  },

  mounted(){
    window.addEventListener('scroll', this.handleScroll);

    window.onscroll = () => {
      this.bottomOfWindow =  (window.pageYOffset  + window.innerHeight  ) > (document.body.scrollHeight -100);
      console.log('ssss', this.bottomOfWindow)
      console.log('inner', window.innerHeight)
      console.log('page', window.pageYOffset)
      if (this.bottomOfWindow) {
        // if (this.noMoreFeed || this.isFeedLoading || this.loadMoreFeed || this.$route.name == 'post-id') {
        //   return;
        // }
        
        // if(this.$route.name == 'profile-user-tab' || this.$route.name == 'search-tab'  || this.$route.name == 'group-group-tab' || this.$route.name == 'page-user-tab' || this.$route.name == 'events-event-tab'){
        //    this.fetchMoreProfileFeed();
        // }else{
        //    this.fetchNewFeed();
        // }
      }
    };

    console.log('ss', this.scrollY)
  },
}
</script>