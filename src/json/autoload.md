---
layout: php
title: "PHP composer 활용 - json 오토로드 설정"
breadcrumb:
- composer
---

# json 설정 : 오토로드 부분
---
`composer.json` 파일에는 패키지들의 `의존성`과 `오토로드 처리`를 위한 설정항목을 추가 관리합니다.  

오토로드는 일반적인 `autoload`와 개발모드시 동작하는 `autoload-dev`로 나누어 집니다.  
`composer.json`파일에 다음과 같은 항목들이 키:값 형태로 삽입된 것을 볼 수 있습니다.  

```json
"autoload":{
        "psr-4":{

        },
        "files":[],
        "classmap":[],        
    },
"autoload-dev":{

}
```

또한 `autoload` 항목은 크게 3개로 나누어 집니다.  

* psr4
* files
* classmap

<br>


## PSR4
---

<br>

## Files
---
오토로드 필드의 또다른 항목으로 files가 있습니다. 이 항목은 배열로 구성이 되어 있습니다.

오토로드에서 PSR-4와 차이점은 무었일까요? PSR-4와 레거시 프로젝트간의 분리가 필요한 경우 있습니다.

다음과 같이 일반적인 PHP 파일을 하나 생성을 합니다.

App\function.php
```php
<?php
    function bindString($str1, $str2) {
        return $str1 . $str2;
    }
?>
```

생성한 파일의 정보를 composer.json 의 오토로드 필드 항목에 추가합니다.
```
"files": [
            "app/function.php"
        ]
```

`Dumpautoload`를 실행하여 컴포저를 갱신합니다.

func.php
```
<?php

require "vendor/autoload.php";

$strings = bindString("hello ", "world");
echo $strings;
```

결과
```
hello world
```


## ClassMap
---
`classmap`은 컴포저가 오토로드를 처리하는 또 다른 방법으로 `PSR4`와 매우 유사합니다. 
이는 `서브폴더의 처리방식`에 있어서 차이점이 있습니다.

사용방법은 아래와 같습니다. 
클래스맵은 재귀적으로 클래스 디렉토리를 

```json
"classmap": [
            "app/classes"
]
```
와 같이 추가합니다. 컴포저의 `dumpautoload`를 실행하여 갱신을 합니다.

이렇게 추가한 클래스들은 다음과 같이 php 파일을 사용하여 오토로드를 할 수 있습니다.  

```php
<?php
require "vendor/autoload.php";

$class1 = new Class1(); // classmap 안에 있는 클래스을 오토로드 합니다.
$class2 = new Class2();
$class3 = new Class3();
```

`클래스맵`은 `/vendor/composer/autoload_classmap.php` 파일을 별도로 생성하여 관리하게 됩니다.

<br>