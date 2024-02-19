# Unreal4 프로젝트

## 다운로드 경로 : https://drive.google.com/file/d/1hQpKN0N8yv1xxGIqA83RunRG0k-Em7d3/view?usp=drive_link

<strong>Unreal Version : Unreal 4.24.3<br/> 
<strong>프로젝트 목적 : Unreal 4 기능 Blueprint 기능의 숙달과 이를 바탕으로 프로그래밍 심화를 하기 위하여 BluePrint 기능만을 사용한 프로젝트 제작

## All Play Video
[![Video Label](http://img.youtube.com/vi/7PDlvy-wnq0/0.jpg)](https://youtu.be/7PDlvy-wnq0)

## Technical Manual

## - Option 

> 샘플게임에 유의하여 간단하게 게임 유저 세팅에 적용 현재 옵션마다 바로 확인을 위하여 바로 적용이 되게끔 수정하였고 추후 하단부 게임유저세팅에 적용하는 Apply Setting 으로 전체 적용되게끔 예정
대부분 위와 같은 형식으로 언리얼에서 제공하는 API를 이용하여 옵션 기능 구현

![Option-ezgif com-video-to-gif-converter](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/778d77f2-fdda-463d-98b0-82b32ec734c8)

![Option](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/2df9c018-a9f5-4e5e-8926-030304930ca0)

## - Inventory System

> BPC_Inventory
> Actor Component로써 L1_Character에 추가 게임에 추가된 아이템들이 L1_Character를 통해 BPC_Inventory 접근 하도록 설계
> ● Add Item
> ● Use Item
> ● Remove Item
> ● Drop Item
> ● Update Inventory Slots
> ● Add More Slots

![UnrealHorrorGame64PCD3D_SM52024-02-1823-17-52-ezgif com-video-to-gif-converter (2)](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/638fb7f6-8b05-45b8-9f4b-44428b250d61)

![Inventory](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/6f7f6e2a-3d69-4bc7-b613-4cd54fa3ea69)


## - Quest

> S_ObjectiveData 구조체를 생성
> IDName / Name
> ObjectiveTitle / Text
> ObjectiveCompleted / Bool
> 형식의 구조체를 생성 L1_GameState를 통하여 퀘스트 시스템을 관리하게끔 설계

![UnrealHorrorGame (64-bit Development PCD3D_SM5)  2024-02-18 오후 1_38_48](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/c40b2521-73b4-4219-86e4-12eb4e0b0d2a)
![UnrealHorrorGame (64-bit Development PCD3D_SM5)  2024-02-18 오후 1_39_02](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/1a18ee52-b540-4e89-9089-72a901c5426d)
![UnrealHorrorGame (64-bit Development PCD3D_SM5)  2024-02-18 오후 1_39_08](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/a04cc2a6-b568-4872-b014-75e8ae33fab1)

![image](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/b13ec00b-4816-4038-b639-359717fcafda)
![image](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/cab148b0-9639-4f98-9744-2c90be299ed6)

> Quest 구조도
> 1. BPI_Objective_Call (SetNextObjective<다음 퀘스트> / CompleteObjectiveCall<퀘스트 완료 후 다음 퀘스트>) 인터페이스 생성 L1_GameState BP에 해당 인터페이스 이벤트 함수 구현
> 2. 퀘스트 상황에 맞는 BP에 BPI_Objective_Call 구현 후 퀘스트 상황에 맞는 Interface 메시지 생성 *타깃은 GameState 설정
> 3. L1_Gamestate에 Interface 메시지가 전달되면 상황에 맞게 처리

## - AI

![AI-ezgif com-video-to-gif-converter](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/706c2715-c322-4b7f-ac52-a20f1971720d)


![AI](https://github.com/showhohxc/Unreal4-FirstPersonView/assets/98040028/c089da04-1a37-4d18-87c6-0c4d1e1d1ee3)
