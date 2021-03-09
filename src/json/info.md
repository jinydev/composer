---
layout: php
title: "PHP composer 활용 - json 설정구조 알아보기"
breadcrumb:
- composer
---

## 패키지 기본정보 설정하기
---
컴포저는 생성한 패키지가 누가, 어떻게 제작을 하고 배포하는지에 대한 기본 정보들을 `composer.json` 파일에 담아 같이 배포하게 됩니다.  
  
이룰 위한 기본 정보 설정 항목들에 대해서 알아 보도록 합니다.  

<br>

## Name 항목
---
`name` 항목은 배포하는 패키지의 이름을 지정합니다. 패키지의 이름은 밴더명과 패키지명의 조합으로 이름을 작성합니다.  
밴더는 배포자의 고유한 아이디 이며, 패키지명은 배포하고자 하는 코드의 별칭 입니다. 이 두개의 값의 조합은 `/`를 구분으로 연결한 문자열 입니다.  

다은은 name을 설정하는 예 입니다.
```json
"name": "jiny/core",
```
이름을 지정할 때에는 스페이스를 포함하지 않습니다.

<br>

## Description
---
패키지에 대한 설명문구를 작성합니다.

```json
"description":"jiny composer website study",
```

<br>

## authors
---
패키지를 작성한 개발자의 정보를 입력 합니다. `authors`항목은 복수의 값을 지정하는 배열 형식 입니다.  
다음과 같이 여러명의 개발자 정보를 같이 등록 할 수 있습니다.  

```json
"authors": [
    {
        "name": "hojinlee",
        "email": "infohojin@gmail.com"
    },
    {
        "name": "hojinlee",
        "email": "infohojin@gmail.com"
    }
]
```

만일 여러명의 개발자로 저자명을 등록을 하고 싶다면은 배열 형태로 추가 하시면 됩니다.

<br>

## homepage
---
패키지 배포와 관련된 홈페이지의 주소를 같이 작성할 수 있습니다.

```json
"homepage": "https://hojin.io",
```

<br>