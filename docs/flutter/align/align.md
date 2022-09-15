---
layout: default
title: 정렬 속성
parent: align
grand_parent: flutter
nav_order: 1
---

## SafeArea
- SafeArea 는 코딩으로 제작된 영역을 모바일 화면의 상단의 알림창, 시간 하단의 홈버튼 영역과 같은 시스템 영역의 경계를 조정할 수 있는 위젯이다.

## MainAxisAlignment : 주축 정렬
- start : 시작
- end : 끝
- center : 가운데
- spaceBetween - 위젯과 위젯사이가 동일하게 배치된다.
- spaceEvenly - 위젯을 같은 간격을 배치하지만 끝과 끝에도 위젯이 아닌 빈 간격으로 시작한다.
- spaceAround - spaceEvenly + 끝과 끝 간격은 1/2 이다.

## CrossAxisAlignment : 반대축 정렬
- start : 시작
- center : default 
- stretch : 강제로 넓이 만큼 늘어남

## MainAxisSize 
- min : 최대 축사이즈 (화면상의 Column, Row 최대값)
- max : 최소 축사이즈 (여백이 없는 각 Row, Column)

## Expanded, Flexible
- Column 과 Row 안에서만 사용이 가능하다.
- 선언된 **영역의 사이즈를 무시**하고, 영역을 화면의 비율에 맞추어 채울수 있다.
- flex 라는 속성을 사용하여, Expanded 가 선언된 영역끼리의 비율을 맞출 수 있다.

## Flexible
- Column 과 Row 안에서만 사용이 가능하다.
- **선언된 영역의 사이즈를 보존** 하고, 나머지 공간을 여백으로 둔다. 
