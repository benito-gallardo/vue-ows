<template>
  <header>
    <nav class="container">
      <ul class="nav-links-left margin-0">
        <li><a href="/" class="logo"><img src="@/static/images/global/color-logo.svg" width="160" height="34" alt=""></a></li>
        <li v-for="navLink in navLinksLeft" :key="navLink.title" :class="{ hasChildren: navLink.sublinks }" class="pos-r">
          <a :to="navLink.url">{{navLink.title}}</a>
          <ul v-if="navLink.sublinks" class="pos-a">
            <li v-for="sublink in navLink.sublinks" :key="sublink.title" class="pos-r">
              <a :to="sublink.url">
                <span v-if="sublink.icon" class="nav-icon-wrap">
                  <svg class="nav-icon " :class="sublink.icon">
                    <use :xlink:href="'#' + sublink.icon"></use>
                  </svg>
                </span>
                <p><span>{{sublink.title}}</span>{{sublink.text}}</p>
              </a>
            </li>
          </ul>
        </li>
      </ul>
      <ul class="nav-links-right margin-0">
          <li class="text-blue-grey text-darken-1 lets-chat"><span>Let's Chat </span><a href="tel:+18006463517">1-800-646-3517</a></li>
          <li><a href="/login" class="login">Login</a></li>
          <li><a class="btn btn-small text-white" href="/free-trial">Get Started</a></li>
      </ul>
    </nav>
    <BaseNavIcons />
    
  </header>
</template>
<script>
import BaseNavIcons from '@/components/BaseNavIcons'
export default {
  components: {
    BaseNavIcons
  },
  data() {
    return {
      navLinksLeft: [
        {title: 'Features', url:'/features'},
        {title: 'Pricing', url:'/features'},
        {title: 'Themes', url:'/features'},
        {title: 'Customers', url:'/features'},
        {title: 'Resources', url:'/features',
          sublinks: [
            { title: 'Help Center', url:'https://help.volusion.com', icon:'icon-help', text: 'Reference expertly-written support articles and tutorials' },
            { title: 'Blog', url:'/blog', icon:'Test', text: 'Fresh ecommerce insights' },
            { title: 'Guides', url:'/guides', icon:'Test', text: 'Comprehensive guides and online business resources' },
            { title: 'Marketing Services', url:'/marketing-services', icon:'Test', text: 'Attract customers to your site with a custom marketing plan' },
            { title: 'Site Design Services ', url:'/design-services', icon:'Test', text: 'Our in-house design team will create the perfect site for you' }
          ]
        }
      ]
    };
  }
};
</script>
<style lang="scss" scoped>
  nav {
    height: 75px;
    padding:0 .5rem;
    display:flex;
    align-items: center;
    justify-content: center;
    justify-content: space-between;
    width: 90%;
    max-width: 1600px;
    font-size:1rem;
    > ul {
      display: flex;
      align-items: center;
      justify-content: center;
      li {
        padding:0 10px;
        &.hasChildren {
          > ul {
            display: none;
            li a {
              display: flex;
              justify-content: center;
              align-content: center;
              .nav-icon-wrap {
                font-size:2.5rem;
                .nav-icon {
                  display: inline-block;
                  width: 1em;
                  height: 1em;
                  stroke-width: 0;
                  
                  fill: currentColor;
                }
              }
            }
          }
          &:hover > ul {
            display: block;
          }
        }
        a {
          color:#546e7a;
          transition:color .3s ease;
          &:hover{
            color: color('green',base);
          }
        }
      }
    &.nav-links-right {
      li {
        &.lets-chat {
          span {
            @media screen and (max-width:1320px){
              display: none;
            }
          }
          @media screen and (max-width:1037px){
            display: none;
          }
        }
      }
     }
    }
  }
</style>
