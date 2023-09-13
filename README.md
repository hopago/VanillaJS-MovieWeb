# VanillaJS-MovieWeb

// Responsive Arrow Click
console.log(Math.floor(window.innerWidth / 270)); // 270px is each movie-list-item width

arrows.forEach((arrow, index) => {

    const lastImgNumber = movieLists[index].querySelectorAll("img").length;

    let clickCounter = 0;

    arrow.addEventListener("click", () => {

        const ratio = Math.floor(window.innerWidth / 270);

        clickCounter++;

        // (5 - ratio)는 클라이언트가 가로길이를 줄였을 때 최대 화면 초기값 5에서 가로길이를 줄임으로써 전시가 되지 않는 아이템 갯수이다
        // +를 한 이유는 전시되지 않는 아이템들만큼 클릭을 더 할 수 있도록 한 것
        if(lastImgNumber - (5 + clickCounter) + (5 - ratio) > 0) {
          movieLists[index].style.transform = `translateX(${
              movieLists[index].computedStyleMap().get("transform")[0].x.value - 300
          }px)`;
        } else {
            movieLists[index].style.transform = "translateX(0)";
            clickCounter = 0;
        }

    });

});

반응형 CSS + JS 설계 함수
