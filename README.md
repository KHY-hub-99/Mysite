# 📌 IntersectionObserver 개요

`IntersectionObserver API`는 대상 요소(target element)가 상위 요소(ancestor element) 또는 뷰포트(viewport)와 교차하는(intersecting) 변화를 비동기적으로 관찰할 수 있는 방법을 제공하는 웹 API입니다. 이 API는 특히 스크롤 이벤트를 사용하여 요소를 감시할 때 발생하는 성능 문제를 해결하기 위해 설계되었습니다.

# 💡 예제 코드 설명

`IntersectionObserver`를 사용하여 스크롤 위치에 따라 내비게이션 메뉴 항목을 하이라이트하는 일반적인 패턴입니다.

1. **요소 선택:**

   - `sections`: `id` 속성을 가진 모든 `<section>` 요소를 선택합니다 (페이지의 콘텐츠 섹션).
   - `menuItems`: 클래스가 `.header_menu_item`인 모든 메뉴 링크를 선택합니다.

2. **Observer 생성:**

   - `new IntersectionObserver(...)`를 생성하며, `{ threshold: 0.2 }` 옵션을 사용하여 섹션의 **20%**가 뷰포트에 들어올 때마다 콜백을 실행하도록 설정합니다.

3. **Callback 로직:**

   - `entries.forEach((entry) => { ... })`로 교차 상태가 변경된 각 요소를 처리합니다.
   - `if (entry.isIntersecting)`: 현재 섹션이 뷰포트에 진입했을 경우에만 실행합니다.
   - `const id = entry.target.getAttribute("id");`: 현재 진입한 섹션의 `id`를 가져옵니다.
   - `menuItems.forEach((item) => item.classList.remove("active"));`: 모든 메뉴 항목에서 `active` 클래스를 제거합니다.
   - `menuItem.classList.add("active");`: 현재 섹션의 `id`에 해당하는 메뉴 항목을 찾아 `active` 클래스를 추가하여 하이라이트합니다.

4. **관찰 시작:**

   - `sections.forEach((section) => observer.observe(section));`: 페이지의 모든 섹션에 대해 관찰을 시작합니다.

# 📝 스크롤 이벤트 기능

코드 스니펫,내용 (설명),주요 역할
"const header = document.querySelector("".header"");",.header 클래스를 가진 HTML 요소를 변수 header에 할당합니다.,DOM 요소 선택
"window.addEventListener(""scroll"", () => { ... });",브라우저 창에서 스크롤 이벤트가 발생할 때마다 중괄호 내의 함수를 실행하도록 등록합니다.,이벤트 리스너 등록
if (window.scrollY > 150) { ... },현재 페이지의 수직 스크롤 위치(window.scrollY)가 150px를 초과하는지 확인합니다.,스크롤 임계점 확인
"header.classList.add(""scrolled"");","스크롤 위치가 150px를 초과하면, header 요소에 **scrolled**라는 CSS 클래스를 추가합니다.",스타일 적용
"header.classList.remove(""scrolled"");","스크롤 위치가 150px 이하로 돌아오면, header 요소에서 scrolled 클래스를 제거합니다.",스타일 원복
