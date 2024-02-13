## TODO : 231115 현재 까지의 진행상황
- Item 창 추가
- Item 구조체와 Inventory Item 구조체 추가 하여 BPC_Inventory 에서 관리하게끔 수정
- 현재까지의 결과 : 필드에 나와있는 아이템을 획득 시 현재 Inventory에 있는 아이템창이 Update되어 배열에 반영된다.

## S_ItemData - Struct
![S_ItemData](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/60d963a8-fe70-4a1d-b688-2676b64bd8fa)
기본적인아이템 구조체를 추가
ItemName - Name   
Icon - Texture2D[Object Reference]   
MaxStackAmount - int    
![S_ItemData_Detail](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/0cd3d586-8c55-4f7b-93b5-16b6be2047b8)

## S_InventoryItems - Struct
Item - BP_Inventoryitem_Master   
Amount - int   
BPC_Inventory 컴포넌트에서 S_Inventory_Item 타입의 InventorySlots 변수를 생성
![S_InventoryItems](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/de27c4fd-0563-4fa4-9c5c-29015f85a96a)

## BP_Inventoryitem_Master
인벤토리 아이템의 부모 클래스
S_Item_Data 구조체 타입의 변수를 생성 - ItemData
-> 자손 클래스인 BP_Inventoryitem_Master_FlashlightBattery 생성후 데이터값 삽입
![BP_Inventoryitem_Master](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/21dbe97f-1fa5-4915-83a6-17330b82311d)

## BP_PickupActor_Mater
획득 아이템의 부모 클래스 
item - BP_InventoryItem_Master  
Amount - Int
-> 자손 클래스인 BP_PickupActor_Flashlight_Master 생성 Item = BP_Inventoryitem_Master_FlashlightBattery / Amount = 1
![BP_PickupActor_Master](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/7d16c10d-23bf-43f1-b917-79585e316137)

## 정리 BP_Inventoryitem_Master-(자손클래스)->BP_Inventoryitem_Master_FlashlightBattery ex) 내 소지품에 배터리를 몇개까지 가질수있는지 세팅 // BP_PickupActor_Mater-(자손클래스)->BP_PickupActor_Flashlight_Master ex) 배터리 아이템 기본 세팅

### Inventory 아이템 구조체 추가
item - BP Inventoryitem Master   
Amount - Item Count   
생성한 Item 구조체를 BP_Inventoryitem_Master 클래스를 통하여 구조체를 ItemData로 변수화 그 후 S_InventoryItems 구조체를 생성후 item을 BP_Inventoryitem_Master 타입으로 변경   
### **지금까지 정리 
#### ItemData 생성 -> ItemData를 BP_Inventoryitem_Master 클래스의 변수 타입으로 추가 -> Item Data를 추가하였으니 현재 플레이어의 Inventory에 Item 정보 갱신을 위한 S_InventoryItems 구조체를 생성
![S_InventoryItems_Detail](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/1ba6ef04-d162-4742-9a5f-4e1883c741d9)

## BPC_Inventory
### Actor Component로써 Inventory 시스템 중요한 마스터 키 Invertory Component 로써 전체적인 Inventory 시스템을 관리한다.
![BPC_Inventory](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/d505a117-dbc8-4d48-aeb8-c41815ec4d0a)
초기 세팅 1. S_InventoryItem 구조체 형식의 변수를 추가 후 PlayerControleer에서 Slots Count를 가져와 Resize()
![BPC_Inventory_Detail_1](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/b0361501-7520-4599-a6e5-0c94eb777ced)
초기 세팅 2. * AddItem
게임에서 획득한 아이템에 대한 정보값을 추가
![BPC_Inventory_Detail_3](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/95b3dafe-01f6-492c-8564-0bb420c1b091)
초기 세팅 3. CheckForEmptySlot 메소드 추가 비어있는 슬롯을 체크하는 메소드 기능 제작
-> 아이템을 획득시 현재 내 인벤토리에 아이템이 들어갈수 있는 자리가 있는지 체크하는 메소드
![BPC_Inventory_Detail_2](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/df641066-f196-4363-a011-ee0eeee84af3)

Ex) 필드에 BP_Inventoryitem_Master_FlashlightBattery 아이템을 플레이어가 획득시 BP_Inventoryitem_Master_FlashlightBattery에서 OnComponentOverlap을 호출 획득한 아이템 자신의 정보를 BPC_Inventory의 AddItem에 정보값을 넘겨준다.
참고 : BP_PickupActor_Master의 값들은 BP_Inventory_Master 값들을 기반으로 생성
AddItem에서는 획적한 정보의 데이터값둘울 Local 데이터값으로 저장 후에 CheckForEmptySlot 함수를 호출하여 내 인벤토리에 남는자리가 있는지 확인한다. 그 후 저장된 Local데이터값 기반으로 S_InventoryItems 구조체를 통하여 InventorySlots에 삽입하여 인벤토리에 데이터를 저장한다.

![W_Inventory_Slot](https://github.com/showhohxc/Unreal-Portfolio/assets/98040028/7c9334ed-6ee5-43f5-8348-45b70234670e)



