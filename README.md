# Wepy-router ![](https://img.shields.io/badge/wepy-router-orange.svg)



### Install
  ``` javascript
  npm i wepy-router --save
  ```  
### Config & Init
  **app.wepy**  
  ``` javascript
  import Router from 'wepy-router'  
  const config = {
    pages: ['pages/index'],
    subPackages: [
      {
        root: 'pages/common',
        pages: ['a', 'b']
      },
    ],
    window: {
      backgroundTextStyle: 'light',
      navigationBarBackgroundColor: '#fff',
      navigationBarTitleText: 'xxx',
      navigationBarTextStyle: 'black'
    }
  }
  export default class extends wepy.app {
    config = config;
    router = new Router(config);
    globalData = {};
    constructor() {
      super()
      this.use('requestfix') 
    }
    onLaunch() {
      console.log(wepy.$router)
    }
  }
  ```
### Useing in page or component   
  **[default navigate]**    
  ``` javascript
  wepy.$router.push('/pages/common/a', {
    id: 1
  })
  ```
  or    
  ``` javascript
  wepy.$router.push({
    path: '/pages/common/a',
    query: {
      id: 1
    }
  })
  ```   
  use by name
  ``` javascript
  wepy.$router.push({
    name: 'CommonA'
  })
  ```
  **[reLaunch]**   
  ``` javascript
  wepy.$router.push({
    path: '/pages/common/b',
    relaunch: true
  })
  ```  
  or  
  ``` javascript
  wepy.$router.push(path: '/pages/common/a',{},true)
  ```
  **[navigate back or front]**   
  > Back to last page  
  ``` javascript
  wepy.$router.go(-1)
  ```    
  > Going front  

  ``` javascript
  wepy.$router.go(1)
  ``` 
  >> You won't be caring about if it should be switching tabbar   
  >> More than pages length have disposed

### More 
  >> if you want to use _this_ insdead of _wepy.$router_ 

  ``` javascript
  import { routerMinx } from 'wepy-router'  
  export default class Index extends wepy.page {
    mixins = [routerMinx]
    onLoad() {
      conosle.log(this.$router)
    }
  }
  ```   
  or  
  ``` javascript
  import {withRouter} from 'wepy-router'  
  @withRouter  
  export default class Index extends wepy.page {
    onLoad() {
      conosle.log(this.$router)
    }
  }
  ```
### License
  [ISC](https://choosealicense.com/licenses/isc/)
  



