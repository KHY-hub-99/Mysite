# ✨ IntersectionObserver

코드 ↓

<script>
const sections = document.querySelectorAll("section[id]");
const menuItems = document.querySelectorAll(".header_menu_item");

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              const id = entry.target.getAttribute("id");
              const menuItem = document.querySelector(
                `.header_menu_item[href="#${id}"]`
              );

              menuItems.forEach((item) => item.classList.remove("active"));
              if (menuItem) menuItem.classList.add("active");
            }
          });
        },
        { threshold: 0.2 }
      );

      sections.forEach((section) => observer.observe(section));
    </script>

1. 화면에 section이 보이면
2. 그 section의 id를 읽고
3. 해당 id와 동일한 메뉴 href를 가진 메뉴를 찾아 반환한다

이후 active 클래스를 붙여서 메뉴 하이라이트가 바뀌는 구조가 된다.
