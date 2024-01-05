# GSAP-ParallaxEffect
GSAP는 JavaScript를 기반으로 한 강력한 애니메이션 라이브러리<br>
GSAP을 사용하면 웹 페이지의 다양한 요소들을 부드럽고 멋진 애니메이션으로 만들 수 있다.<br>
GSAP의 Parallax 효과는 웹 페이지의 여러 레이어가 서로 다른 속도로 스크롤될 때 생기는 입체적인 시각 효과를 만들어내는 기능<br>

## 설치
- CDN을 통해 스크립트 추가
```js
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.2/dist/gsap.min.js"></script>
```
- npm install를 통해 설치   
```js
npm install gsap
```
- ScrollTrigger 추가
```js
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
```
## GSAP Parallax Effect01

<details>

 <summary>GSAP scrollTrigger - 애니메이션 기본 효과</summary>

<br>
box1 - 360도 회전하면서 오른쪽으로 500정도 가면서 동그랗게 변하기<br> 
<br>  
box2 - trigger: box2, box2가 화면에 나타날때 애니메이션이 시작 <br>
<br>
box3 - toggleActions: "play none reverse none": 트리거가 활성화되면 애니메이션을 재생하고,다른 트리거 액션이 없으며, 트리거가 비활성화되면 애니메이션을 역재생하지 않고 유지 <br>
<br>
box4 - start: "top 50%": 트리거의 시작 위치를 화면 상단에서 50% 지점으로 설정 , end: "bottom 20%": 트리거의 끝 위치를 화면 하단에서 20% 지점으로 설정 , markers: false: ScrollTrigger의 디버깅을 위한 마커를 표시하지 않음.<br>
<br>
box5 - scrub: true: 스크롤 속도에 따라 애니메이션을 부드럽게 조절하는 설정을 활성화,  box5 요소가 화면에 나타날 때, 스크롤 속도에 따라 부드럽게 애니메이션이 진행<br>
<br>
box6 - pin: true: 트리거가 활성화될 동안 요소를 고정시키는 설정을 활성화, box6 요소가 화면에 나타나면 스크롤 속도에 따라 부드럽게 애니메이션이 진행되며, 동시에 pin 옵션에 의해 화면에 고정되어 나타난 후 스크롤이 특정 위치(bottom:400px)에 도달하면 다시 해제<br>
<br>
box7 - toggleClass:"active", box7가 화면에 나타날 때 2초 동안의 애니메이션 효과가 적용되고, 스크롤 이벤트에 따라 부드럽게 제어되면서 "active" 클래스가 토글<br>
<br>
box8 - box8이 화면에 나타날 때, 스크롤 속도에 따라 부드럽게 애니메이션이 진행되며, 다양한 ScrollTrigger 이벤트 콜백이 발생할 때마다 콘솔에 해당 메시지를 출력 <br>
<br>

```js
<script>
    const box1 = document.querySelector("#section1 .parallax__item__img");
    const box2 = document.querySelector("#section2 .parallax__item__img");
    const box3 = document.querySelector("#section3 .parallax__item__img");
    const box4 = document.querySelector("#section4 .parallax__item__img");
    const box5 = document.querySelector("#section5 .parallax__item__img");
    const box6 = document.querySelector("#section6 .parallax__item__img");
    const box7 = document.querySelector("#section7 .parallax__item__img");
    const box8 = document.querySelector("#section8 .parallax__item__img");
    const box9 = document.querySelector("#section9 .parallax__item__img");

    // 01
    gsap.to(box1, {
        duration : 2,
        x: 500,
        borderRadius: 100,
        rotation:360
    });

    // 02 : trigger
    gsap.to(box2, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        scrollTrigger: {
            trigger: box2
        }
    });

    // 03 :toggleActions
    gsap.to(box3, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        scrollTrigger: {
            trigger: box3,
            toggleActions:"play none reverse none" // play pause resume restart complete none
                                                    // onEnter onLeave onEnterBack onLeaveBack
        }
    });

    // 04 : start, end
    gsap.to(box4, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        
        scrollTrigger: {
            trigger: box4,
            start: "top 50%",
            end: "bottom 20%",
            toggleActions:"play none reverse none",
            markers: false
        }
    });

    // 05: scrub
    gsap.to(box5, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        
        scrollTrigger: {
            trigger: box5,
            start: "top 50%",
            end: "bottom 20%",
            scrub: true  
        }
    });

    // 06: pin
    gsap.to(box6, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        
        scrollTrigger: {
            trigger: box6,
            start: "top 50%",
            end: "bottom 400px",
            scrub: true, 
            pin: true 
        }
    });

    // 07 : toggleClass
    gsap.to(box7, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        
        scrollTrigger: {
            trigger: box7,
            start: "top center",
            end: "bottom 20%",
            scrub: true, 
            toggleClass:"active",
            id:"box7",
            markers: true
        }
    });
    
    // 08. : callback
    gsap.to(box8, {
        duration: 2,
        x: 500,
        rotation: 360,
        borderRadius: 100,
        
        scrollTrigger: {
            trigger: box8,
            start: "top center",
            end: "bottom 20%",
            scrub:true, 
            onEnter: () => {console.log("onEneter")},
            onLeave: () => {console.log("onEneter")},
            onEnterBack:() => {console.log("onEneterBack")},
            onLeaveBack:() => {console.log("onLeaveBack")},
            onUpdat: (self) => console.log("onUpdate", self.progress.toFixed(3)),
            onToggle: (self) => console.log("onToggle", self.isActive)
        }
    });
    
</script>
```
</details>

## GSAP Parallax Effect02

<details>

<summary>GSAP scrollTrigger - Pin 애니메이션</summary>

<br>
ani1 - section1 내부의 .parallax__item__img 요소에 대한 애니메이션을 추가, 이미지는 회전값이 720도가 되고, 크기가 0으로 축소되며, 경계 반경이 200으로 설정
이어서 이미지에 대한 다음 애니메이션을 추가해서, 이미지는 다시 초기 회전값인 0으로 돌아가며, 크기는 1로 확대되고, 경계 반경은 20으로 설정, 현재 스크롤 위치에서 2000px 아래로 스크롤할 때 애니메이션이 끝남.<br> 
<br>  
ani2 - i1, i2, i3 이미지는 y축 방향으로 -200만큼 이동하면서 나타나며, autoAlpha 속성을 이용하여 투명도를 0에서 1로 증가시킵니다. 또한, 이미지의 경계 반경도 200으로 설정, 스크롤될 때 순차적으로 i1이미지, i2이미지, i3이미지 등장하는 이미지 애니메이션<br>
<br>
ani3 - autoAlpha: 0: 이미지의 투명도를 0으로 설정하여 처음에는 화면에 보이지 않도록 하고, ease: "back.out(4)": 애니메이션의 이동 효과에 이징 함수를 적용하여 물리적인 효과를 부여합니다. 여기서는 뒤로 튀기는(back) 효과를 사용하고, 효과의 강도는 4로 설정, from: "random"은 ani2 에서는 1,2,3 순서대로 이미지가 나왔다면,
ani3은 1,3,2 or 2,1,3 등등 랜덤으로 이미지 나옴. <br>
<br>
ani4 - scale: 2: 이미지를 2배로 확대, width: "100vw": 이미지의 너비를 화면의 가로 크기와 동일하게 설정, height: "100vh": 이미지의 높이를 화면의 세로 크기와 동일하게 설정, 현재 스크롤 위치에서 3000px 아래로 스크롤할 때 애니메이션이 끝나고, 이미지가 화면에 나타나면서 2배로 확대되고, 스크롤 중에 축소되면서 특정 위치에서 고정되는 애니메이션<br>
<br>
ani5 - .to("#section5 .t1",{xPercent: 300},"text"): section5 내의 .t1 클래스를 가진 텍스트 요소에 대한 애니메이션을 추가, 텍스트는 x축 방향으로 300%만큼 이동하고,.to("#section5 .t2",{xPercent: -300},"text"): section5 내의 .t2 클래스를 가진 텍스트 요소에 대한 애니메이션을 추가, 텍스트는 x축 방향으로 -300%만큼 이동하면서, section5 내의 텍스트 요소들이 좌우로 이동하면서 나타나는 애니메이션<br>
<br>
ani6 - .to("#section6 .parallax__item__text",{scale:60, duration: 2}): section6 내의 .parallax__item__text 클래스를 가진 텍스트 요소에 대한 애니메이션을 추가하고, 텍스트는 60배로 확대되며, 이 애니메이션은 2초 동안 진행<br>
<br>
ani7 - .from() 메서드를 사용하여 .t2, .t3, ..., .t7에 대한 각각의 텍스트 요소에 대한 애니메이션을 추가하고, 각 텍스트는 투명도가 0에서 1로, y축 방향으로 50만큼 이동하면서 나타나게 되고, 각각의 애니메이션은 이전 애니메이션이 끝난 후 1초씩 지연되어 시작 , section7 내의 여러 텍스트 요소들이 제자리에서 차례대로 나타나는 애니메이션<br>
<br>
ani8 - section8 내의 텍스트 및 이미지가 특정 방향으로 이동하면서 나타나는 애니메이션을 설정, 첫 번째 텍스트는 화면의 오른쪽에서 왼쪽으로 이동하고, 두 번째 텍스트는 화면의 왼쪽에서 오른쪽으로 이동하고, 3번째 텍스트는 화면의 오른쪽에서 왼쪽으로 이동하고, 마지막 이미지는 오른쪽에서 왼쪽으로 이동하면서 동시에 360도 회전하고, 5.5배로 확대되어 나타납니다.<br>
<br>
ani9 - section9 내의 이미지가 2초 동안 60배로 확대되면서 나타나고, 그 후에 투명도를 갖게 되어 사라지는 애니메이션을 구현합니다. 이 애니메이션은 스크롤 중에 특정 위치에서 시작되며, 해당 section이 스크롤되는 동안 이미지가 고정되어 나타남.<br>
<br>

```js
<script>
       // 01 : 이미지 애니메이션 주기
        const ani1 = gsap.timeline();
        ani1.to("#section1 .parallax__item__img" , {rotation:720, scale: 0, borderRadius: 200})
            .to("#section1 .parallax__item__img" , {rotation:0, scale: 1, borderRadius: 20})
        
        ScrollTrigger.create({
            animation: ani1,
            trigger: "#section1",
            start:"top top",
            end:"+=2000",
            scrub:true,
            pin: true,
            anticipatePin: 1,
            markers: true
        });
        
        
        // 02 : 이미지를 순차적으로 나오기
        const ani2 = gsap.timeline();
        ani2.from("#section2 .i1", {y: -200, autoAlpha:0, borderRadius: 200})
            .from("#section2 .i2", {y: -200, autoAlpha:0, borderRadius: 200})
            .from("#section2 .i3", {y: -200, autoAlpha:0, borderRadius: 200})

        ScrollTrigger.create({
            animation: ani2,
            trigger:"#section2",
            start: "top top",
            end: "+=2000",
            scrub:true,
            pin: true,
            anticipatePin: 1,
        })

        // 03 : 이미지를 랜덤으로 나오기
        const ani3 = gsap.timeline();
        ani3.from("#section3 .parallax__item__img", {
            autoAlpha: 0,
            y: -100,
            ease: "back.out(4)",
            // stagger: 0.1
            stagger: {
                amount:1,
                from: "random"
            }
        });

        ScrollTrigger.create({
            animation: ani3,
            trigger:"#section3",
            start:"top top",
            end: "+=3000",
            scrub: true,
            pin: true
        })

        // 04 : 이미지 축소하기
        const ani4 = gsap.timeline();
        ani4.from("#section4 .parallax__item__img",{
            autoAlpha: 0,
            scale: 2,
            width: "100vw",
            height: "100vh"
        })

        ScrollTrigger.create({
            animation: ani4,
            trigger:"#section4",
            start:"top top",
            end: "+=3000",
            scrub: true,
            pin: true
        })

        // 05 : 텍스트 애니메이션
        const ani5 = gsap.timeline();
        ani5.to("#section5 .t1",{xPercent: 300} ,"text")
            .to("#section5 .t2",{xPercent: -300},"text")
            .to("#section5 .t3",{xPercent: 300}, "text")
            .to("#section5 .t4",{xPercent: -300},"text")
        
        ScrollTrigger.create({
            animation: ani5,
            trigger:"#section5",
            start:"top top",
            end: "+=3000",
            scrub: true,
            pin: true,
        })
        
        // 06 : 텍스트 확대
        const ani6 = gsap.timeline();
        ani6.to("#section6 .parallax__item__text",{scale:60, duration: 2})
            .to("#section6 .parallax__item__text",{autoAlpha : 0})
        
        ScrollTrigger.create({
            animation: ani6,
            trigger:"#section6",
            start:"top top",
            end: "+=4000",
            scrub: true,
            pin: true,
        })
        
        
        // 07 : 텍스트 제자리 애니메이션
        const ani7 = gsap.timeline();
        ani7.from("#section7 .t1", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t2", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t3", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t4", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t5", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t6", {autoAlpha: 0, duration:1, y:50}, "+=1")
            .from("#section7 .t7", {autoAlpha: 0, duration:1, y:50}, "+=1")

        ScrollTrigger.create({
            animation: ani7,
            trigger:"#section7",
            start:"top top",
            end: "+=6000",
            scrub: true,
            pin: true,
        })

        // 08 : 텍스트 애니메이션
        const ani8 = gsap.timeline();
        ani8.from("#section8 .t1",{x:innerWidth * 1})
            .from("#section8 .t2",{x:innerWidth * -1})
            .from("#section8 .t3",{x:innerWidth * 1})
            .from("#section8 .i1",{x:innerWidth * 1 , rotation: 360, scale: 5.5})
        
        ScrollTrigger.create({
            animation: ani8,
            trigger:"#section8",
            start:"top top",
            end: "+=6000",
            scrub: true,
            pin: true,
            anticipatePin: 0,
            markers: true
        })

        // 09. 이미지 확대
        const ani9 = gsap.timeline();
        ani9.to("#section9 .parallax__item__img",{scale:60, duration: 2})
            .to("#section9 .parallax__item__img",{autoAlpha : 0})
            
        ScrollTrigger.create({
            animation: ani9,
            trigger:"#section9",
            start:"top top",
            end: "+=4000",
            scrub: true,
            pin: true,
        })

    </script>
```
</details>

## GSAP Parallax Effect03

<details>

<summary>GSAP scrollTrigger - 배경 고정시키기 </summary>

<br>
1. ScrollTrigger 플러그인을 사용하여 페이지에서 #section5라는 요소를 지정한 section으로 고정시키는 애니메이션을 만들고, section이 페이지의 상단에 도달하면 고정되며, markers: true 설정으로 디버깅을 위한 마커를 활성화<br>
<br>
2. 여러 section에 대해 반복문을 통해 ScrollTrigger 플러그인을 생성하여 각각의 section을 페이지에서 고정시키는 애니메이션을 만들고, .parallax__item 클래스를 가진 모든 요소에 대해 고정 트리거를 생성하고, 각 section이 페이지의 상단에 도달하면 고정됩니다. pinSpacing: false는 각 section 사이의 공간을 없애고 연속적으로 고정되도록 함.<br>
<br>
3. panels 배열은 .parallax__item 클래스를 가진 모든 요소를 저장합니다.<br>
tops 배열은 각 섹션에 대한 ScrollTrigger를 생성하여 시작 위치를 저장합니다.<br>
각 섹션에 대해 새로운 ScrollTrigger를 생성하고, 섹션의 높이가 창 높이보다 작으면 섹션 상단을 기준으로, 그렇지 않으면 섹션 하단을 기준으로 고정시킵니다.<br>
마지막으로, ScrollTrigger.create 함수를 사용하여 페이지 전체의 스냅 효과를 설정합니다. 이 효과는 섹션의 시작 위치를 기준으로 페이지를 일정 간격으로 이동시킵니다.<br>

```js
 <script>
        // 01. 한개 section 고정시키기
        const panel = document.querySelector("#section5");

        ScrollTrigger.create({
            trigger:panel,
            start: "top top",
            pin: true,
            markers: true
        });

        // 02. 여러개 section 고정시키기
        gsap.utils.toArray(".parallax__item").forEach((panel,i) => {
            ScrollTrigger.create({
                trigger: panel, 
                start: "top top",
                pin: true,
                pinSpacing: false
            })
        });

        // 03. 스냅 고정 효과 만들기
        let panels = gsap.utils.toArray(".parallax__item");
        let tops = panels.map(panel => ScrollTrigger.create({trigger: panel, start: "top top"}));

        panels.forEach((panel, i) => {
            ScrollTrigger.create({
                trigger: panel,
                start: () => panel.offsetHeight < window.innerHeight ? "top top" : "bottom bottom",
                pin: true, 
                pinSpacing: false 
            });
        });

        ScrollTrigger.create({
            snap: {
                snapTo: (progress, self) => {
                    let panelStarts = tops.map(st => st.start), 
                    snapScroll = gsap.utils.snap(panelStarts, self.scroll()); 
                    return gsap.utils.normalize(0, ScrollTrigger.maxScroll(window), snapScroll); 
                },
                duration: 0.5
            }
        });

        
    </script>

```
</details>

## GSAP Parallax Effect04

<details>

<summary>GSAP scrollTrigger - 이질감 효과</summary>

<br>


```js
  <script>
        // 01. 이질감 표현하기
        gsap.to(".parallax__item__desc", {
            yPercent: -100,
            ease: "none",
            duration: 0.5,
            scrollTrigger: {
                trigger: ".parallax__item__desc",
                start: "top bottom",
                end: "bottom top",
                markers: true,
                scrub: true
            }
        })

        // 02. 여러개 이질감 표현하기
        gsap.utils.toArray(".parallax__item__desc").forEach(item => {
            gsap.to(item, {
                yPercent: -200,
                ease: "none",
                duration: 0.5,
                scrollTrigger: {
                    trigger: item,
                    start: "top bottom",
                    end: "bottom top",
                    markers: true,
                    scrub: 0.5
                }
            })
        });
    </script>

```
</details>

    