# 3d-devTools

ENOVIA(3DEXPERIENCE) 개발용 도구 배포 파일입니다. 파일명은 고정이며 항상 최신 버전입니다.

| 도구 | 버전 | 다운로드 | 설명 |
| --- | --- | --- | --- |
| 3D Inspector | 0.22.2 | [3d-inspector.zip](https://github.com/LeeOuHyoun/3d-devTools/raw/main/3d-inspector.zip) | 위젯 화면에 로드된 소스를 검색하는 크롬 개발자도구 확장 |
| 3D MQL Console | 0.0.81 | [3d-mql-console.vsix](https://github.com/LeeOuHyoun/3d-devTools/raw/main/3d-mql-console.vsix) | ENOVIA MQL 세션을 편집기 탭에서 사용하는 VS Code 확장 |
| 3D MQL Graph | 0.0.108 | [3d-mql-graph.vsix](https://github.com/LeeOuHyoun/3d-devTools/raw/main/3d-mql-graph.vsix) | ENOVIA MQL로 객체와 관계를 그래프로 탐색하는 VS Code 확장 |

## 3D Inspector 설치

1. zip을 고정된 위치(예: `C:\tools\3d-inspector`)에 압축을 풉니다.
2. 크롬에서 `chrome://extensions`를 열고 오른쪽 위 **개발자 모드**를 켭니다.
3. **압축해제된 확장 프로그램을 로드합니다**를 누르고 압축을 푼 폴더를 선택합니다.
4. 3DEXPERIENCE 페이지를 새로고침합니다.

업데이트할 때는 새 zip을 같은 폴더에 덮어 풀고 `chrome://extensions`에서 새로고침 버튼을 누릅니다.

## 3D MQL Console / 3D MQL Graph 설치

VS Code 확장 보기(`Ctrl+Shift+X`) 오른쪽 위 `...` → **VSIX에서 설치...** 로 vsix 파일을 선택합니다.

또는 터미널에서 설치합니다.

```
code --install-extension 3d-mql-console.vsix
code --install-extension 3d-mql-graph.vsix
```

업데이트할 때도 같은 방법으로 새 vsix를 설치합니다.
