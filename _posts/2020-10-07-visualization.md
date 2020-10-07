---
title: '[Handy Hints 01] matplotlib 한글 설정'
excerpt: "한글 깨짐 현상 해결 방법"

toc: true
toc_label: "Table of Contents"
toc_sticky: true
categories:
  - Handy_Hints
tags:
  - Python
  - Visualization
  - Matplotlib
last_modified_at: 2020-10-07
---


matplotlib의 기본 설정 폰트는 한글을 지원하지 않습니다.

한글이 포함된 그래프를 그리면 한글이 깨져서 나옵니다.

이를 해결하기 위한 방법이 크게 두 가지가 있습니다.

## 1. 설정파일 변경 (재설정하기 전까지 영구적으로 변경!!)

### 1. OS에 설치된 폰트명 조회

  설정파일을 변경하기 전 우선 캐시 파일을 삭제합시다.  
  아래 코드를 실행하면 캐시파일이 어디에 저장되어 있는지 알려줍니다.

  ```python
  >>> import matplotlib as mpl
  >>> import matplotlib.font_manager as fm

  >>> mpl.get_cachedir()
  'C:\\Users\\(경로)\\.matplotlib'
  ```

  그 폴더에서 font 관련 cache 파일을 삭제해주세요.  
  전체 폰트 리스트를 확인하기 위해 다음 코드를 실행해주세요.

  ```python
  >>> for font in fm.fontManager.ttflist:
  >>>	  print(font.name, font.fname)  # 폰트이름, 포트파일경로
  ```

  어마어마하게 많은 폰트 정보가 출력됩니다.  
  모든 폰트가 다 필요하지 않으니 우리가 원하는 폰트명을 검색해봅시다.

  ```python
  [(font.name, font.fname) for font in fm.fontManager.ttflist if 'malgun' in font.name.lower()]
  ```

  저는 맑은 고딕체로 설정해주려고 malgun을 찾았습니다.  
  원하는 폰트가 있으면 그 폰트를 검색하시면 됩니다.  
  전체 폰트 리스트에서 확인하세요.

### 2. matplotlib 환경 설정에서 폰트 변경하기

  다음 코드는 matplotlib의 설정파일 경로를 알려줍니다.

  ```python
  >>> mpl.matplotlib_fname()
  'C:\\Users\\(경로)\\anaconda3\\envs\\ml\\lib\\site-packages\\matplotlib\\mpl-data\\matplotlibrc'
  ```

  마지막의 matplotlibrc이 설정파일입니다.  
  문서 편집기(메모장, 워드패드 등)에서도 위 파일을 편집할 수 있습니다.  
  Visual Studio Code 혹은 Atom이 설치되어 있다면 그 프로그램을 통해서도 편집 가능합니다.  
  편하신 방법으로 설정하시면 됩니다.  
  폰트 관련 설정은 아래와 같습니다.

  ```markdown
  font.family:Malgun Gothic
  # optional
  # 아래는 변경하지 않아도 괜찮습니다.
  # font.size:12
  # xtick.labelsize:12
  # ytick.labelsize:12
  # axes.labelsize:12  
  # axes.unicode_minus:False
  ```

  위와 같이 변경하면 그래프를 그릴 때 한글이 포함되어 있어도 언제나 깨짐 없이 잘 나옵니다.

## 2. 함수를 이용해 변경
### 1. matplotlib 함수로 폰트 변경하기

  ```python
  import matplotlib as mpl
  from matplotlib import font_manager as fm

  # 한글 폰트 설정
  font_name = fm.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()

  mpl.rcParams["font.family"] = font_name
  mpl.rcParams["font.size"] = 15
  mpl.rcParams['xtick.labelsize'] = 12
  mpl.rcParams['ytick.labelsize'] = 12
  mpl.rcParams['axes.labelsize'] = 15
  # tick의 음수기호 '-' 가 깨지는 것 처리
  mpl.rcParams['axes.unicode_minus'] = False
  ```

  matplotlib의 font_manager를 통해 원하는 font 이름을 가져올 수 있습니다.  
  matplotlib의 rcParams를 통해 원하는 설정들을 변경해 줄 수 있습니다.

  눈치 빠르신 분들은 벌써 아시겠지만, 설정파일에서 변경했던 설정 이름들과  
  rcParams에서 변경하는 설정 변경 이름이 동일합니다.  
  마치 dictionary를 사용하는 것처럼 ```rcParams['이름']``` 을 통해서  
  설정을 변경할 수 있습니다.

  주피터노트북 등 편집기를 통해 작업할 경우 편집기를 매번 시작할 때마다  
  위 코드를 실행해줘야 하는 번거로움이 발생합니다.

  다만, 영어를 더 많이 사용하여 시각화를 할 경우 설정파일을 변경하지 않고도  
  한글 시각화를 깔끔하게 구현할 수 있으니 참고하여 사용하면 됩니다.

  이상 matplotlib에서 한글 깨짐 현상을 해결하는 방법을 정리해보았습니다.
