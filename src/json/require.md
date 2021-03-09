---
layout: php
title: "PHP composer 활용 - 의존성 설정"
breadcrumb:
- composer
---

# 패키지 의존성
---
컴포저의 하나의 패키지는 복수의 다른 패키지들과 `의존성`을 가질 수 있습니다.  
이를 의해서 관련된 의존관계를 `composer.json` 설정안에 추가할 수 있습니다.  

의존성을 설정할때에는 `require`항목을 추가합니다. require는 크게 일반용과 개발용인 `require-dev`가 있습니다.

* require
* require-dev 

<br>

## require
---
실제적인 페키지들의 목록이 나열되어 있습니다. 또한, 패키지가 다른 패키지와 의존관계가 있는 경우 같이 적어 주시면 됩니다.

다음은 illuminate/support 패키지의 require부분입니다.

```json
"require": {
        "php": "^7.1.3",
        "ext-mbstring": "*",
        "doctrine/inflector": "~1.1",
        "illuminate/contracts": "5.6.*",
        "nesbot/carbon": "^1.24.1"
    }
```

패키지의 PHP 적용 버전을 지정할 수 있습니다. 또한 의존 패키지들 목록과 버전을 같이 지정을 합니다.

<br>

## require-dev
require-dev는 Require와 유사하지만 차이점은 개발과 실제서버의 페키지를 분리하는 것입니다.  
require-dev는 개발모드일 때 같이 설치되는 페키지들을 나열합니다.

```json
"require-dev": {
    
}
```
<br>