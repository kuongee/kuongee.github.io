# 구현

AUI widget들의 custom build를 위한 Grunt file을 작성한다.

grunt --widget={ path of widget.json } 형태로 빌드를 실행할 수 있다.

#### Gruntfile 외부에서 제공받는 정보 <a id="CustomBuild&#xB97C;&#xC704;&#xD55C;Gruntfile-Gruntfile&#xC678;&#xBD80;&#xC5D0;&#xC11C;&#xC81C;&#xACF5;&#xBC1B;&#xB294;&#xC815;&#xBCF4;"></a>

* dependency.json
* widgetmap\_sorted.json
* widget.json

#### Gruntfile 구현 내용 <a id="CustomBuild&#xB97C;&#xC704;&#xD55C;Gruntfile-Gruntfile&#xAD6C;&#xD604;&#xB0B4;&#xC6A9;"></a>

Dependency 알고리즘 구현

```text
/* 선택된 위젯들의 dependency를 가진 모든 위젯들을 찾아냄 */
// dependencyJson: 위젯의 dependency 정보를 가지고 있는 객체
// selectedWidgets: 빌드 요청이 들어온 위젯들의 리스트
function getAllDependentWidget(grunt, dependencyJson, selectedWidgets) {
    const checkList = selectedWidgets; // 위젯들의 모든 dependency를 확인할 수 있게 하는 리스트
    const dependentWidgets = []; // 최종적으로 빌드에 포함할 위젯들을 저장하는 리스트
 
 
    while (checkList.length > 0) {
        // checkList에서 item(위젯)을 하나씩 꺼내어 모든 위젯들의 dependency를 확인할 수 있도록 함
        const checkItem = checkList.shift();
        if (dependentWidgets.indexOf(checkItem) < 0) {
            // 꺼낸 item은 중복되지 않으면 최종 결과 리스트에 넣음
            dependentWidgets.push(checkItem);
        }
 
        const dependentItems = dependencyJson[checkItem]; // 꺼낸 item과 dependency 있는 widget들
        for (let d = 0; d < dependentItems.length; d++) {
            const dItem = dependentItems[d];
            // dependency가 있는 widget들의 dependency도 확인하기 위해 중복되지 않으면 checkList에 추가
            if (dependentWidgets.indexOf(dItem) < 0 && checkList.indexOf(dItem) < 0) {
                checkList.push(dItem);
            }
        }
    }
 
    return dependentWidgets;
}
```

