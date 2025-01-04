## pre-commit으로 black과 isort 적용
커밋한 파일이 python **black**과 **isort**로 PEP 8 형식에 맞게 자동으로 재작성해주도록 합니다. 해당 과정은 VSCODE 및 개인 환경에서 적용되었음을 사전에 밝힙니다.

-----
### 1. 생성한 프로젝트 Repository를 VSCODE내에서 Clone
```bash
git clone SSH key
git remote -v
git remote rename origin upstream
```
git clone을 진행해줬기 때문에 git init을 할 필요가 없습니다.
### 3. pre-commit 설치
```bash
pip install pre-commit
pre-commit install
```
### 4. 프로젝트 디렉토리 내 .pre-commit-config.yaml 파일 추가
```yaml
repos:
  - repo: https://github.com/psf/black
    rev: 24.10.0
    hooks:
      - id: black
        args: ["--quiet"]

  - repo: https://github.com/pycqa/isort
    rev: 5.13.2
    hooks:
      - id: isort
        name: isort (python)
```
### 5. 포맷팅 적용할 파일 status에 추가 후 커밋 진행
#### 적용 이전 코드
```python
import pandas as pd
print( "this is test file.")
ls = ["this", 
"is",   "test",
"file"]
def PRINT():
    test =       "let's see how working this code"
    print( test)
PRINT( )
```
#### 적용 이후 코드
```python
import pandas as pd

print("this is test file.")
ls = ["this", "is", "test", "file"]


def PRINT():
    test = "let's see how working this code"
    print(test)


PRINT()
```
-----

***위와 같이 commit을 했을 때 적용된 것을 알 수 있습니다. 이후 status에 다시 추가하여 commit을 다시 진행하면 됩니다.***

### 시도 중
***black과 isort 적용 후 status에 자동으로 올라가서 가장 최근 커밋메세지로 재커밋하는 작업은 시도도 중에 있습니다.***

##### 최근 업데이트 : 250105