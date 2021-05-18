---
title: 文字背景粒子特效
author: Luckey
coverImg: /medias/banner/7.jpg
top: false
cover: false
toc: true
mathjax: false
summary: '一款jQuery+CSS3的文字背景粒子动画特效，一共6种粒子效果，每种文字背景的粒子效果都不同，有漂浮的有坠落的等等。 '
tags:
  - jQuery+CSS3
  - 粒子特效
categories:
  - 前端篇
abbrlink: 4b3510a4
reprintPolicy: cc_by
date: 2020-03-27 00:00:00
img:
password:
---

### 前言

一款jQuery+CSS3的文字背景粒子动画特效，一共6种粒子效果，每种文字背景的粒子效果都不同，有漂浮的有坠落的等等。 

### 0x001 特效演示

---

<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" ><span class="particletext fire" style="font-size:48px;position: relative;">This is fires</span></div>


<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > <span class="particletext lines" style="font-size:48px; position: relative;">This is lines</span>
</div>

<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" ><span class="particletext hearts" style="font-size:48px; position: relative;">This is hearts</span></div>

<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > <span class="particletext bubbles" style="font-size:48px; position: relative;">This is bubbles</span>
</div>

<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > <span class="particletext confetti" style="font-size:48px; position: relative;">This is confetti</span>
</div>

<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > <span class="particletext sunbeams" style="font-size:48px; position: relative;">This is sunbeams</span>
</div>

<style>

.particletext {
  
}

.fire > .particle {
  position: absolute;
  background-color: rgba(255, 193, 7, 0.5);
  border-radius: 40px;
  border-top-right-radius: 0px;
  -webkit-animation: fires 0.8s linear infinite;
          animation: fires 0.8s linear infinite;
  -webkit-transform: rotate(-45deg);
          transform: rotate(-45deg);
  opacity: 0;
}
/*css keyframes 动画*/
@-webkit-keyframes fires {
  0% {
    -webkit-transform: rotate(-70deg) translateY(0%);
            transform: rotate(-70deg) translateY(0%);
  }
  25% {
    -webkit-transform: rotate(-20deg) translateY(-5%);
            transform: rotate(-20deg) translateY(-5%);
    opacity: 1;
  }
  50% {
    -webkit-transform: rotate(-70deg) translateY(-10%);
            transform: rotate(-70deg) translateY(-10%);
  }
  75% {
    -webkit-transform: rotate(-20deg) translateY(-20%);
            transform: rotate(-20deg) translateY(-20%);
  }
  100% {
    -webkit-transform: rotate(-70deg) translateY(-40%);
            transform: rotate(-70deg) translateY(-40%);
    opacity: 1;
  }
}
@keyframes fires {
  0% {
    -webkit-transform: rotate(-70deg) translateY(0%);
            transform: rotate(-70deg) translateY(0%);
  }
  25% {
    -webkit-transform: rotate(-20deg) translateY(-5%);
            transform: rotate(-20deg) translateY(-5%);
    opacity: 1;
  }
  50% {
    -webkit-transform: rotate(-70deg) translateY(-10%);
            transform: rotate(-70deg) translateY(-10%);
  }
  75% {
    -webkit-transform: rotate(-20deg) translateY(-20%);
            transform: rotate(-20deg) translateY(-20%);
  }
  100% {
    -webkit-transform: rotate(-70deg) translateY(-40%);
            transform: rotate(-70deg) translateY(-40%);
    opacity: 1;
  }
}
</style>


<script type="text/javascript" src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script>
function fire() { 
   $.each($(".particletext.fire"), function(){ 
      var firecount = ($(this).width()/50)*20; 
      for(var i = 0; i <= firecount; i++) { 
         var size = $.rnd(8,12); 
         $(this).append('<span class="particle" style="top:' + $.rnd(40,70) + '%; left:' + $.rnd(-10,100) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,20)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<style>
.lines > .particle {
  position: absolute;
  background-color: rgba(244, 67, 54, 0.5);
  -webkit-animation: lines 3s linear infinite;
          animation: lines 3s linear infinite;
}
@-webkit-keyframes lines {
  0%, 50%, 100% {
    -webkit-transform: translateY(0%);
            transform: translateY(0%);
  }
  25% {
    -webkit-transform: translateY(100%);
            transform: translateY(100%);
  }
  75% {
    -webkit-transform: translateY(-100%);
            transform: translateY(-100%);
  }
}
@keyframes lines {
  0%, 50%, 100% {
    -webkit-transform: translateY(0%);
            transform: translateY(0%);
  }
  25% {
    -webkit-transform: translateY(100%);
            transform: translateY(100%);
  }
  75% {
    -webkit-transform: translateY(-100%);
            transform: translateY(-100%);
  }
}
</style>

<script>
function lines() { 
   $.each($(".particletext.lines"), function(){ 
      var linecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= linecount; i++) { 
         $(this).append('<span class="particle" style="top:' + $.rnd(-30,30) + '%; left:' + $.rnd(-10,110) + '%;width:' + $.rnd(1,3) + 'px; height:' + $.rnd(20,80) + '%;animation-delay: -' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<style>
.hearts > .particle {
  opacity: 0;
  position: absolute;
  background-color: #cc2a5d;
  -webkit-animation: hearts 3s ease-in infinite;
          animation: hearts 3s ease-in infinite;
}
.hearts > .particle:before,.hearts > .particle:after {
  position: absolute;
  content: '';
  border-radius: 100px;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  background-color: #cc2a5d;
}
.hearts > .particle:before {
  -webkit-transform: translateX(-50%);
          transform: translateX(-50%);
}
.hearts > .particle:after {
  -webkit-transform: translateY(-50%);
          transform: translateY(-50%);
}
@-webkit-keyframes hearts {
  0% {
    opacity: 0;
    -webkit-transform: translate(0, 0%) rotate(45deg);
            transform: translate(0, 0%) rotate(45deg);
  }
  20% {
    opacity: 0.8;
    -webkit-transform: translate(0, -20%) rotate(45deg);
            transform: translate(0, -20%) rotate(45deg);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%) rotate(45deg);
            transform: translate(0, -1000%) rotate(45deg);
  }
}
@keyframes hearts {
  0% {
    opacity: 0;
    -webkit-transform: translate(0, 0%) rotate(45deg);
            transform: translate(0, 0%) rotate(45deg);
  }
  20% {
    opacity: 0.8;
    -webkit-transform: translate(0, -20%) rotate(45deg);
            transform: translate(0, -20%) rotate(45deg);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%) rotate(45deg);
            transform: translate(0, -1000%) rotate(45deg);
  }
}
</style>




<script>
function hearts() { 
   $.each($(".particletext.hearts"), function(){ 
      var heartcount = ($(this).width()/50)*5; 
      for(var i = 0; i <= heartcount; i++) { 
         var size = ($.rnd(60,120)/10); 
         $(this).append('<span class="particle" style="top:' + $.rnd(20,80) + '%; left:' + $.rnd(0,95) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<style>
.bubbles > .particle {
  opacity: 0;
  position: absolute;
  background-color: rgba(33, 150, 243, 0.5);
  -webkit-animation: bubbles 3s ease-in infinite;
          animation: bubbles 3s ease-in infinite;
  border-radius: 100%;
}
@-webkit-keyframes bubbles {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 1;
    -webkit-transform: translate(0, -20%);
            transform: translate(0, -20%);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%);
            transform: translate(0, -1000%);
  }
}

@keyframes bubbles {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 1;
    -webkit-transform: translate(0, -20%);
            transform: translate(0, -20%);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%);
            transform: translate(0, -1000%);
  }
}
</style>





<script>
function bubbles() { 
   $.each($(".particletext.bubbles"), function(){ 
      var bubblecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= bubblecount; i++) { 
         var size = ($.rnd(40,80)/10); 
         $(this).append('<span class="particle" style="top:' + $.rnd(20,80) + '%; left:' + $.rnd(0,95) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<style>
.confetti > .particle {
  opacity: 0;
  position: absolute;
  -webkit-animation: confetti 3s ease-in infinite;
          animation: confetti 3s ease-in infinite;
}
.confetti > .particle.c1 {
  background-color: rgba(76, 175, 80, 0.5);
}
.confetti > .particle.c2 {
  background-color: rgba(156, 39, 176, 0.5);
}
@-webkit-keyframes confetti {
  0% {
    opacity: 0;
    -webkit-transform: translateY(0%) rotate(0deg);
            transform: translateY(0%) rotate(0deg);
  }
  10% {
    opacity: 1;
  }
  35% {
    -webkit-transform: translateY(-800%) rotate(270deg);
            transform: translateY(-800%) rotate(270deg);
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    -webkit-transform: translateY(2000%) rotate(1440deg);
            transform: translateY(2000%) rotate(1440deg);
  }
}
@keyframes confetti {
  0% {
    opacity: 0;
    -webkit-transform: translateY(0%) rotate(0deg);
            transform: translateY(0%) rotate(0deg);
  }
  10% {
    opacity: 1;
  }
  35% {
    -webkit-transform: translateY(-800%) rotate(270deg);
            transform: translateY(-800%) rotate(270deg);
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    -webkit-transform: translateY(2000%) rotate(1440deg);
            transform: translateY(2000%) rotate(1440deg);
  }
}
</style>




<script>
function confetti() { 
   $.each($(".particletext.confetti"), function(){ 
      var confetticount = ($(this).width()/50)*10; 
      for(var i = 0; i <= confetticount; i++) { 
         $(this).append('<span class="particle c' + $.rnd(1,2) + '" style="top:' + $.rnd(10,50) + '%; left:' + $.rnd(0,100) + '%;width:' + $.rnd(6,8) + 'px; height:' + $.rnd(3,4) + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<style>
.sunbeams > .particle {
  position: absolute;
  background-color: rgba(253, 216, 53, 0.5);
  -webkit-animation: sunbeams 3s linear infinite;
          animation: sunbeams 3s linear infinite;
}
@-webkit-keyframes sunbeams {
  0% {
    -webkit-transform: translateY(40%) rotate(0deg);
            transform: translateY(40%) rotate(0deg);
  }
  50% {
    -webkit-transform: translateY(-40%) rotate(180deg);
            transform: translateY(-40%) rotate(180deg);
  }
  100% {
    -webkit-transform: translateY(40%) rotate(360deg);
            transform: translateY(40%) rotate(360deg);
  }
  0%,14%,17%,43%,53%,71%,80%,94%,100% {
    opacity: 0;
  }
  6%,15%,24%,28%,48%,55%,78%,82%,99% {
    opacity: 1;
  }
}
@keyframes sunbeams {
  0% {
    -webkit-transform: translateY(40%) rotate(0deg);
            transform: translateY(40%) rotate(0deg);
  }
  50% {
    -webkit-transform: translateY(-40%) rotate(180deg);
            transform: translateY(-40%) rotate(180deg);
  }
  100% {
    -webkit-transform: translateY(40%) rotate(360deg);
            transform: translateY(40%) rotate(360deg);
  }
  0%,14%,17%,43%,53%,71%,80%,94%,100% {
    opacity: 0;
  }
  6%,15%,24%,28%,48%,55%,78%,82%,99% {
    opacity: 1;
  }
}
</style>

<script>
function sunbeams() { 
   $.each($(".particletext.sunbeams"), function(){ 
      var linecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= linecount; i++) { 
         $(this).append('<span class="particle" style="top:' + $.rnd(-50,00) + '%; left:' + $.rnd(0,100) + '%;width:' + $.rnd(1,3) + 'px; height:' + $.rnd(80,160) + '%;animation-delay: -' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 

</script>

<script type="text/javascript">
  function initparticles() { 
      bubbles(); 
      hearts(); 
      lines(); 
      confetti(); 
      fire(); 
      sunbeams(); 
    }
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  initparticles();
</script>

### 0x002 Fires 特效

#### 1. JS 代码

```javascript
<script>
function fire() { 
   $.each($(".particletext.fire"), function(){ 
      var firecount = ($(this).width()/50)*20; 
      for(var i = 0; i <= firecount; i++) { 
         var size = $.rnd(8,12); 
         $(this).append('<span class="particle" style="top:' + $.rnd(40,70) + '%; left:' + $.rnd(-10,100) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,20)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  fire();
</script>
```

#### 2. CSS 代码

```css
<style>
.fire > .particle {
  position: absolute;
  background-color: rgba(255, 193, 7, 0.5);
  border-radius: 40px;
  border-top-right-radius: 0px;
  -webkit-animation: fires 0.8s linear infinite;
          animation: fires 0.8s linear infinite;
  -webkit-transform: rotate(-45deg);
          transform: rotate(-45deg);
  opacity: 0;
}

@-webkit-keyframes fires {
  0% {
    -webkit-transform: rotate(-70deg) translateY(0%);
            transform: rotate(-70deg) translateY(0%);
  }
  25% {
    -webkit-transform: rotate(-20deg) translateY(-5%);
            transform: rotate(-20deg) translateY(-5%);
    opacity: 1;
  }
  50% {
    -webkit-transform: rotate(-70deg) translateY(-10%);
            transform: rotate(-70deg) translateY(-10%);
  }
  75% {
    -webkit-transform: rotate(-20deg) translateY(-20%);
            transform: rotate(-20deg) translateY(-20%);
  }
  100% {
    -webkit-transform: rotate(-70deg) translateY(-40%);
            transform: rotate(-70deg) translateY(-40%);
    opacity: 1;
  }
}
@keyframes fires {
  0% {
    -webkit-transform: rotate(-70deg) translateY(0%);
            transform: rotate(-70deg) translateY(0%);
  }
  25% {
    -webkit-transform: rotate(-20deg) translateY(-5%);
            transform: rotate(-20deg) translateY(-5%);
    opacity: 1;
  }
  50% {
    -webkit-transform: rotate(-70deg) translateY(-10%);
            transform: rotate(-70deg) translateY(-10%);
  }
  75% {
    -webkit-transform: rotate(-20deg) translateY(-20%);
            transform: rotate(-20deg) translateY(-20%);
  }
  100% {
    -webkit-transform: rotate(-70deg) translateY(-40%);
            transform: rotate(-70deg) translateY(-40%);
    opacity: 1;
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" >
<span class="particletext fire" style="font-size:48px;position: relative;">This is fires</span>
</div>
```

### 0x003 Lines 特效

#### 1. JS 代码

```javascript
<script>
function lines() { 
   $.each($(".particletext.lines"), function(){ 
      var linecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= linecount; i++) { 
         $(this).append('<span class="particle" style="top:' + $.rnd(-30,30) + '%; left:' + $.rnd(-10,110) + '%;width:' + $.rnd(1,3) + 'px; height:' + $.rnd(20,80) + '%;animation-delay: -' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  lines();
</script>
```

#### 2. CSS 代码

```css
<style>
.lines > .particle {
  position: absolute;
  background-color: rgba(244, 67, 54, 0.5);
  -webkit-animation: lines 3s linear infinite;
          animation: lines 3s linear infinite;
}
@-webkit-keyframes lines {
  0%, 50%, 100% {
    -webkit-transform: translateY(0%);
            transform: translateY(0%);
  }
  25% {
    -webkit-transform: translateY(100%);
            transform: translateY(100%);
  }
  75% {
    -webkit-transform: translateY(-100%);
            transform: translateY(-100%);
  }
}
@keyframes lines {
  0%, 50%, 100% {
    -webkit-transform: translateY(0%);
            transform: translateY(0%);
  }
  25% {
    -webkit-transform: translateY(100%);
            transform: translateY(100%);
  }
  75% {
    -webkit-transform: translateY(-100%);
            transform: translateY(-100%);
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > 
<span class="particletext lines" style="font-size:48px; position: relative;">This is lines</span>
</div>
```

### 0x004 Hearts 特效

#### 1. JS 代码

```javascript
<script>
function hearts() { 
   $.each($(".particletext.hearts"), function(){ 
      var heartcount = ($(this).width()/50)*5; 
      for(var i = 0; i <= heartcount; i++) { 
         var size = ($.rnd(60,120)/10); 
         $(this).append('<span class="particle" style="top:' + $.rnd(20,80) + '%; left:' + $.rnd(0,95) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  hearts();
</script>
```

#### 2. CSS 代码

```css
<style>
.hearts > .particle {
  opacity: 0;
  position: absolute;
  background-color: #cc2a5d;
  -webkit-animation: hearts 3s ease-in infinite;
          animation: hearts 3s ease-in infinite;
}
.hearts > .particle:before, .hearts > .particle:after {
  position: absolute;
  content: '';
  border-radius: 100px;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  background-color: #cc2a5d;
}
.hearts > .particle:before {
  -webkit-transform: translateX(-50%);
          transform: translateX(-50%);
}
.hearts > .particle:after {
  -webkit-transform: translateY(-50%);
          transform: translateY(-50%);
}
@-webkit-keyframes hearts {
  0% {
    opacity: 0;
    -webkit-transform: translate(0, 0%) rotate(45deg);
            transform: translate(0, 0%) rotate(45deg);
  }
  20% {
    opacity: 0.8;
    -webkit-transform: translate(0, -20%) rotate(45deg);
            transform: translate(0, -20%) rotate(45deg);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%) rotate(45deg);
            transform: translate(0, -1000%) rotate(45deg);
  }
}
@keyframes hearts {
  0% {
    opacity: 0;
    -webkit-transform: translate(0, 0%) rotate(45deg);
            transform: translate(0, 0%) rotate(45deg);
  }
  20% {
    opacity: 0.8;
    -webkit-transform: translate(0, -20%) rotate(45deg);
            transform: translate(0, -20%) rotate(45deg);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%) rotate(45deg);
            transform: translate(0, -1000%) rotate(45deg);
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" >
<span class="particletext hearts" style="font-size:48px; position: relative;">This is hearts</span>
</div>
```

### 0x005 Bubbles 特效

#### 1. JS 代码

```javascript
<script>
function bubbles() { 
   $.each($(".particletext.bubbles"), function(){ 
      var bubblecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= bubblecount; i++) { 
         var size = ($.rnd(40,80)/10); 
         $(this).append('<span class="particle" style="top:' + $.rnd(20,80) + '%; left:' + $.rnd(0,95) + '%;width:' + size + 'px; height:' + size + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  bubbles();
</script>
```

#### 2. CSS 代码

```css
<style>
<style>
.bubbles > .particle {
  opacity: 0;
  position: absolute;
  background-color: rgba(33, 150, 243, 0.5);
  -webkit-animation: bubbles 3s ease-in infinite;
          animation: bubbles 3s ease-in infinite;
  border-radius: 100%;
}
@-webkit-keyframes bubbles {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 1;
    -webkit-transform: translate(0, -20%);
            transform: translate(0, -20%);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%);
            transform: translate(0, -1000%);
  }
}

@keyframes bubbles {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 1;
    -webkit-transform: translate(0, -20%);
            transform: translate(0, -20%);
  }
  100% {
    opacity: 0;
    -webkit-transform: translate(0, -1000%);
            transform: translate(0, -1000%);
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > 
<span class="particletext bubbles" style="font-size:48px; position: relative;">This is bubbles</span>
</div>
```

### 0x006 Confetti 特效

#### 1. JS 代码

```javascript
<script>
function confetti() { 
   $.each($(".particletext.confetti"), function(){ 
      var confetticount = ($(this).width()/50)*10; 
      for(var i = 0; i <= confetticount; i++) { 
         $(this).append('<span class="particle c' + $.rnd(1,2) + '" style="top:' + $.rnd(10,50) + '%; left:' + $.rnd(0,100) + '%;width:' + $.rnd(6,8) + 'px; height:' + $.rnd(3,4) + 'px;animation-delay: ' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  confetti();
</script>
```

#### 2. CSS 代码

```css
<style>
.confetti > .particle {
  opacity: 0;
  position: absolute;
  -webkit-animation: confetti 3s ease-in infinite;
          animation: confetti 3s ease-in infinite;
}
.confetti > .particle.c1 {
  background-color: rgba(76, 175, 80, 0.5);
}
.confetti > .particle.c2 {
  background-color: rgba(156, 39, 176, 0.5);
}
@-webkit-keyframes confetti {
  0% {
    opacity: 0;
    -webkit-transform: translateY(0%) rotate(0deg);
            transform: translateY(0%) rotate(0deg);
  }
  10% {
    opacity: 1;
  }
  35% {
    -webkit-transform: translateY(-800%) rotate(270deg);
            transform: translateY(-800%) rotate(270deg);
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    -webkit-transform: translateY(2000%) rotate(1440deg);
            transform: translateY(2000%) rotate(1440deg);
  }
}
@keyframes confetti {
  0% {
    opacity: 0;
    -webkit-transform: translateY(0%) rotate(0deg);
            transform: translateY(0%) rotate(0deg);
  }
  10% {
    opacity: 1;
  }
  35% {
    -webkit-transform: translateY(-800%) rotate(270deg);
            transform: translateY(-800%) rotate(270deg);
  }
  80% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    -webkit-transform: translateY(2000%) rotate(1440deg);
            transform: translateY(2000%) rotate(1440deg);
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" > 
<span class="particletext confetti" style="font-size:48px; position: relative;">This is confetti</span>
</div>
```

### 0x007 Sunbeams 特效

#### 1. JS 代码

```javascript
<script>
function sunbeams() { 
   $.each($(".particletext.sunbeams"), function(){ 
      var linecount = ($(this).width()/50)*10; 
      for(var i = 0; i <= linecount; i++) { 
         $(this).append('<span class="particle" style="top:' + $.rnd(-50,00) + '%; left:' + $.rnd(0,100) + '%;width:' + $.rnd(1,3) + 'px; height:' + $.rnd(80,160) + '%;animation-delay: -' + ($.rnd(0,30)/10) + 's;"></span>'); 
      } 
   }); 
} 
  jQuery.rnd = function(m,n) {
      m = parseInt(m);
      n = parseInt(n);
      return Math.floor( Math.random() * (n - m + 1) ) + m;
  }
  sunbeams();
</script>
```

#### 2. CSS 代码

```css
<style>
.sunbeams > .particle {
  position: absolute;
  background-color: rgba(253, 216, 53, 0.5);
  -webkit-animation: sunbeams 3s linear infinite;
          animation: sunbeams 3s linear infinite;
}
@-webkit-keyframes sunbeams {
  0% {
    -webkit-transform: translateY(40%) rotate(0deg);
            transform: translateY(40%) rotate(0deg);
  }
  50% {
    -webkit-transform: translateY(-40%) rotate(180deg);
            transform: translateY(-40%) rotate(180deg);
  }
  100% {
    -webkit-transform: translateY(40%) rotate(360deg);
            transform: translateY(40%) rotate(360deg);
  }
  0%,14%,17%,43%,53%,71%,80%,94%,100% {
    opacity: 0;
  }
  6%,15%,24%,28%,48%,55%,78%,82%,99% {
    opacity: 1;
  }
}
@keyframes sunbeams {
  0% {
    -webkit-transform: translateY(40%) rotate(0deg);
            transform: translateY(40%) rotate(0deg);
  }
  50% {
    -webkit-transform: translateY(-40%) rotate(180deg);
            transform: translateY(-40%) rotate(180deg);
  }
  100% {
    -webkit-transform: translateY(40%) rotate(360deg);
            transform: translateY(40%) rotate(360deg);
  }
  0%,14%,17%,43%,53%,71%,80%,94%,100% {
    opacity: 0;
  }
  6%,15%,24%,28%,48%,55%,78%,82%,99% {
    opacity: 1;
  }
}
</style>
```

#### 3. HTML 代码

```html
<div style="width: 100%;text-align: center; height: 120px; position: relative; bottom: 0px;" >
<span class="particletext sunbeams" style="font-size:48px; position: relative;">This is sunbeams</span>
</div>
```