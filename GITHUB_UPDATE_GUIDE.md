# 기존 GitHub Pages 뷰어 수정 배포 방법

## 준비

1. 제공된 ZIP 파일을 내려받습니다.
2. ZIP 압축을 풉니다.
3. 압축을 푼 폴더에서 아래 파일을 확인합니다.

```text
index.html
.nojekyll
README.md
GITHUB_UPDATE_GUIDE.md
```

실제 사이트 작동에 필수인 파일은 `index.html`입니다. PDF 세 개는 이 HTML 안에 이미 포함되어 있으므로 PDF 파일을 따로 올리지 않습니다.

---

## 방법 A - GitHub 웹사이트에서 교체하기

현재 `index.html`은 약 13.5 MiB이므로 GitHub 웹 업로드 한도 25 MiB 이내입니다.

### 1. 기존 저장소 열기

기존에 배포한 GitHub 저장소로 들어갑니다.

예시:

```text
https://github.com/내아이디/all-in-one-pdf-viewer
```

### 2. 저장소 최상단 확인

현재 화면에 기존 `index.html`이 바로 보여야 합니다.

올바른 구조:

```text
저장소 최상단
├─ index.html
└─ README.md
```

잘못된 구조:

```text
저장소 최상단
└─ all-in-one-pdf-viewer
   └─ index.html
```

### 3. 새 파일 업로드

저장소 첫 화면에서 다음 순서로 누릅니다.

```text
Add file
→ Upload files
```

압축을 푼 폴더의 다음 파일을 업로드 영역에 끌어다 놓습니다.

```text
index.html
.nojekyll
README.md
GITHUB_UPDATE_GUIDE.md
```

같은 이름의 `index.html`이 이미 있으면 GitHub가 기존 파일의 변경으로 처리합니다. 업로드 화면에서 `index.html`이 변경 파일로 잡혔는지 확인합니다.

### 4. 변경 사항 저장

아래의 커밋 메시지를 입력합니다.

```text
Update viewer with three textbooks
```

다음을 선택합니다.

```text
Commit directly to the main branch
```

그다음 `Commit changes`를 누릅니다.

### 5. Pages 설정 확인

기존 사이트가 이미 배포되고 있었다면 보통 다시 설정할 필요가 없습니다. 그래도 다음 설정인지 확인합니다.

```text
Settings
→ Pages
```

`Build and deployment` 항목:

```text
Source: Deploy from a branch
Branch: main
Folder: /(root)
```

설정이 다르면 위와 같이 바꾸고 `Save`를 누릅니다.

### 6. 재배포 완료 확인

저장소 상단에서 다음 메뉴를 엽니다.

```text
Actions
```

`pages build and deployment` 작업이 초록색 체크가 되면 배포 완료입니다.

기존 사이트 주소는 그대로 유지됩니다.

```text
https://내아이디.github.io/all-in-one-pdf-viewer/
```

### 7. 이전 화면이 계속 보일 때

브라우저 캐시를 비웁니다.

Windows:

```text
Ctrl + Shift + R
```

Mac:

```text
Command + Shift + R
```

또는 주소 끝에 임시로 다음을 붙여 접속합니다.

```text
?v=2
```

예시:

```text
https://내아이디.github.io/all-in-one-pdf-viewer/?v=2
```

---

## 방법 B - GitHub Desktop으로 교체하기

웹 업로드가 멈추거나 실패하면 GitHub Desktop 방식이 더 안정적입니다.

### 1. GitHub Desktop 실행

GitHub Desktop에서 기존 뷰어 저장소를 선택합니다.

저장소가 컴퓨터에 없다면:

```text
File
→ Clone repository
→ GitHub.com
→ 기존 저장소 선택
→ Clone
```

### 2. 로컬 저장소 폴더 열기

```text
Repository
→ Show in Explorer
```

Mac에서는:

```text
Repository
→ Show in Finder
```

### 3. 파일 덮어쓰기

압축을 푼 새 `index.html`을 로컬 저장소 최상단에 복사합니다.
기존 파일을 새 파일로 덮어씁니다.

함께 복사할 파일:

```text
.nojekyll
README.md
GITHUB_UPDATE_GUIDE.md
```

### 4. 커밋

GitHub Desktop으로 돌아오면 변경 파일이 표시됩니다.

Summary:

```text
Update viewer with three textbooks
```

`Commit to main`을 누릅니다.

### 5. GitHub에 전송

```text
Push origin
```

을 누릅니다. 이후 GitHub Pages가 자동으로 새 버전을 배포합니다.

---

## 배포 후 기능 점검

1. 사이트 첫 화면에서 교재 세 권의 표지가 표시되는지 확인합니다.
2. 수학Ⅰ, 수학Ⅱ, 확률과 통계를 각각 열어봅니다.
3. 상단 책 아이콘을 눌러 교재 선택 화면으로 돌아오는지 확인합니다.
4. `두쪽 책 넘김`에서 페이지가 맞쪽으로 표시되는지 확인합니다.
5. 다음 버튼을 눌렀을 때 책장 넘김 모션이 작동하는지 확인합니다.
6. `두쪽 스크롤`로 바꾸고 두 페이지씩 아래로 스크롤되는지 확인합니다.
7. 모바일에서 `더보기 > 교재 선택`이 작동하는지 확인합니다.
8. 공유 버튼으로 복사한 주소가 선택한 교재와 페이지를 바로 여는지 확인합니다.

---

## 직접 접속 주소

교재 선택 화면:

```text
https://내아이디.github.io/저장소이름/
```

수학Ⅰ 바로 열기:

```text
https://내아이디.github.io/저장소이름/?book=math1
```

수학Ⅱ 바로 열기:

```text
https://내아이디.github.io/저장소이름/?book=math2
```

확률과 통계 바로 열기:

```text
https://내아이디.github.io/저장소이름/?book=stats
```

특정 페이지 바로 열기:

```text
https://내아이디.github.io/저장소이름/?book=math2&page=8
```

두쪽 스크롤 모드로 바로 열기:

```text
https://내아이디.github.io/저장소이름/?book=stats&mode=scroll
```

---

## 문제가 발생할 때

### 사이트가 404일 때

- `index.html`이 저장소 최상단에 있는지 확인합니다.
- `Settings > Pages`가 `main / (root)`인지 확인합니다.
- `Actions`에서 배포 작업이 실패하지 않았는지 확인합니다.

### 업로드가 안 될 때

- ZIP 파일 자체가 아니라 압축을 푼 파일을 올려야 합니다.
- `index.html`을 텍스트 편집기로 열어 복사·붙여넣기 하지 말고 파일 그대로 업로드합니다.
- 웹 업로드가 계속 실패하면 GitHub Desktop 방식을 사용합니다.

### PDF가 흰 화면으로 보일 때

- 인터넷 연결을 확인합니다. PDF 데이터는 HTML 안에 있지만 PDF.js 라이브러리는 CDN에서 불러옵니다.
- 광고 차단기나 보안 확장 프로그램이 `cdn.jsdelivr.net`을 막고 있지 않은지 확인합니다.
- 강력 새로고침 후 다시 접속합니다.
