# ShareTemp

[ppnation](https://ppnation.heohyuk.workers.dev) 사이트 **자료실**의 데이터 저장소입니다.
사이트는 이 레포의 `resources.json` 을 요청 시점에 읽어 자료 목록을 렌더링합니다.
여기에 커밋하면 재배포 없이 몇 분 내 사이트에 반영됩니다.

## 자료 추가 방법

### 1) 파일 자료

1. 파일을 `files/` 폴더에 올린다. (예: `files/lecture-01.pdf`)
2. `resources.json` 의 `items` 배열에 항목을 추가한다.

```json
{
  "title": "1강 - 오리엔테이션",
  "description": "강의 소개와 개발 환경 세팅",
  "category": "강의노트",
  "file": "files/lecture-01.pdf"
}
```

### 2) 외부 링크 자료

`file` 대신 `url` 을 넣는다.

```json
{
  "title": "MDN JavaScript 가이드",
  "description": "자바스크립트 기초 레퍼런스",
  "category": "참고자료",
  "url": "https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide"
}
```

## 필드

| 필드 | 필수 | 설명 |
|------|------|------|
| `title` | O | 자료 제목 |
| `description` | X | 한 줄 설명 |
| `category` | X | 분류. 생략 시 `기타`. 예: `강의노트`, `실습코드`, `참고자료` |
| `file` | 파일이면 O | 레포 기준 상대 경로. `raw.githubusercontent.com` URL 로 변환되어 제공된다. |
| `url` | 링크면 O | 외부 링크 주소 |

> `file` 과 `url` 중 하나는 반드시 있어야 한다. 둘 다 있으면 `file` 이 우선.

## 주의

- **퍼블릭 레포**입니다. 공개해도 되는 자료만 올리세요.
- `resources.json` 은 반드시 유효한 JSON 이어야 합니다. (커밋 전 검증 권장)
- 큰 파일(수십 MB+)은 GitHub 권장 한도(100MB)와 raw 전송 속도를 고려하세요.
- 사이트 쪽 연동 코드: `ppnation` 레포의 `src/lib/resources.ts` (`RESOURCES_REPO`).
