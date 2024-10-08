## Game > Gamebase > 콘솔 사용 가이드 > 쿠폰

게임 운영 시 게임 유저에게 배포할 쿠폰을 대량으로 생성하고 관리할 수 있는 기능입니다.

## Coupon Publish

앱 내에서 사용할 수 있는 쿠폰을 발급 또는 검색할 수 있습니다.

### Search Coupon publish

검색 조건에 맞는 쿠폰 발급 내역을 검색합니다.

![gamebase_coupon_01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_01_240813.png)

**검색 조건**

- **상태**: (필수) 쿠폰의 현재 진행 상태. 전체, 활성, 비활성 선택이 가능합니다.
- **유효 기간**: (필수) 선택한 기간에 사용 가능한 쿠폰 목록을 조회합니다.
- **쿠폰명**: 등록한 쿠폰명을 기준으로 검색합니다.

**검색 결과**

- **쿠폰명**: 발급을 진행한 쿠폰의 이름
- **쿠폰 타입**: 발급을 진행한 쿠폰의 유형
- **지급 아이템**: 발급 시 등록한 아이템 이름, 등록한 아이템이 여러 개이면 대표 아이템 외 N개로 표시
- **스토어**: 쿠폰을 사용할 수 있는 스토어 정보입니다.
- **사용/발급**: 발급한 쿠폰의 총 사용 수량/총 발급 수량 정보
- **유효 기간**: 쿠폰 사용 가능 기간
- **발급 일시**: 발급을 진행한 일시 정보
- **쿠폰 사용 이력**: 발급한 쿠폰의 사용 이력 정보를 검색하도록 화면 이동
- **다운로드**: 발급한 쿠폰의 상세 코드 목록 다운로드
- **지급 아이템**: 발급한 쿠폰의 등록 가능 여부 표시

### Publish coupon

쿠폰 발급 검색 화면에서 **등록** 버튼을 클릭하면 쿠폰 발급을 진행할 수 있습니다.

![gamebase_coupon_02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_02_240813.png)

#### 1. 쿠폰 타입

발급할 쿠폰 타입을 설정할 수 있습니다.
각 타입의 설명은 다음과 같습니다.

- **시리얼** : 임의의 쿠폰 번호를 생성해 쿠폰 코드를 발급합니다.
- **키워드** : 지정된 키워드 이름을 유저가 사용할 수 있는 쿠폰 코드로 발급합니다.

#### 2. 쿠폰명

발급한 쿠폰의 목적을 알 수 있는 쿠폰 이름을 입력합니다.

#### 3. 쿠폰 코드

**키워드 쿠폰 발급 시**에 유저가 사용할 수 있는 고유 쿠폰 코드를 입력합니다.

#### 4. 스토어

발급한 쿠폰을 사용할 수 있는 스토어를 선택합니다.

기본적으로는 전체가 선택되어 있으며 쿠폰 사용을 스토어별로 제한하고자 할 경우 사용을 하길 원하는 스토어를 지정합니다.

#### 5. 유효 기간

발급한 쿠폰을 사용할 수 있는 기간을 설정합니다.

#### 6. 발급 개수

발급 시 생성할 쿠폰 코드의 개수를 설정합니다.
한 번 요청 시 최대 100만 개의 쿠폰 코드까지 생성할 수 있습니다.

#### 7. 유저별 사용 가능 개수

유저 1명이 최대로 사용할 수 있는 쿠폰 개수를 설정합니다.
설정할 수 있는 최대 개수는 99개입니다. 무제한으로 사용하게 하려면  0으로 설정합니다.

#### 8. 아이템

쿠폰 코드 등록 시 지급할 아이템 정보를 입력합니다.
지급할 아이템을 선택하고 오른쪽에 지급 개수를 입력합니다.
아이템을 등록하려면 쿠폰 아이템 메뉴에서 먼저 아이템을 등록해야 선택할 수 있습니다.


> [참고]
>
> 쿠폰 아이템을 등록하는 방법은 [Coupon Item](./oper-coupon/#coupon-item)을 참고하시기 바랍니다.


### Update publish coupon

발급한 쿠폰 정보를 수정하려면 상세 정보에서 **수정** 버튼을 클릭합니다.
이미 발급한 쿠폰 코드 타입은 수정할 수 없으므로 새 타입의 쿠폰을 발급하려면 발급 정보를 새로 등록해야 합니다.

![gamebase_coupon_03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_03_240813.png)

#### 1. 쿠폰명

발급한 쿠폰의 목적을 알 수 있는 쿠폰 이름을 입력합니다.

#### 2. 스토어

발급한 쿠폰을 사용할 수 있는 스토어를 선택합니다.
발급시 선택한 스토어가 선택되어 있으며 정보를 변경할 경우 변경한 스토어에서만 발급된 쿠폰을 사용할 수 있게 됩니다.

#### 3. 유효 기간

발급한 쿠폰을 사용할 수 있는 기간을 설정합니다.

#### 4. 유저별 사용 가능 개수

유저 1명이 최대로 사용할 수 있는 쿠폰 개수를 설정합니다.
설정할 수 있는 최대 개수는 99개입니다. 무제한으로 사용하게 하려면  0으로 설정합니다.

#### 5. 아이템

쿠폰 코드 등록 시 지급할 아이템 정보를 입력합니다.
지급할 아이템을 선택하고 오른쪽에 지급 개수를 입력합니다.
아이템을 등록하려면 **쿠폰 아이템** 메뉴에서 먼저 아이템을 등록해야 선택할 수 있습니다.

#### 6. 쿠폰 발송
발급된 쿠폰 정보를 이용하여 유저에게 직접 쿠폰을 발송할 수 있는 기능을 제공합니다.

![gamebase_coupon_04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_04_240813.png)
##### (1) 발송 유형 : 발송 유형을 선택합니다. MMS/SMS를 지원하며 MMS의 경우 제목을 추가로 입력하여 발송해야 합니다.

##### (2) 템플릿 선택 : NHN Cloud SMS 서비스에서 템플릿을 등록하셨다면 해당 템플릿을 선택하여 발송할 수 있습니다. 등록된 템플릿이 없다면 선택하지 않아도 됩니다.

##### (3) 광고성 여부 : 발송하고자 하는 SMS의 광고성 여부를 선택합니다. 광고성으로 보내고자 할 경우 (광고), [무료수신거부] 문자열이 포함되어야 SMS를 발송할 수 있으니 발송 시 유의바랍니다.

##### (4) 발송 번호 : NHN Cloud SMS에 등록한 발송 번호를 선택할 수 있습니다. 이 번호는 수신자에게 발송자 번호로 보여지게 됩니다.

##### (5) 발송 타입 : 즉시/예약 발송을 선택할 수 있으며 즉시 발송일 경우 발송 버튼을 누르는 즉시 SMS가 발송되며 예약 발송의 경우 지정된 시간에 SMS가 발송됩니다.

##### (6) 제목 : MMS 발송 시 해당 MMS의 제목을 지정합니다. MMS발송일 경우에만 입력할 수 있습니다.

##### (7) 내용 : 발송하고자 하는 상세 내용을 입력합니다. ##code##문자열이 쿠폰으로 치환되는 문자열이며 해당 문자열이 포함되어 있지 않으면 발송이 되지않으니 입력 시 유의 바랍니다.

##### (8) 수신 거부 번호 : NHN Cloud SMS에 등록된 수신 거부 번호를 선택합니다. 광고성 SMS를 발송하고자 할 경우 해당 항목을 내용에 입력해 주셔야 하며 발송화면에서의 선택항목은 참고용으로 보여주기 위해 선택되는 값이므로 발송 시 유의해 주셔야 합니다.

##### (9) 수신 번호 : 수신 대상을 파일을 이용하여 등록합니다. **번호** 또는 **번호/쿠폰** 형식으로 등록할 수 있으며 번호만 입력되었을 경우 배정되는 쿠폰은 발급된 쿠폰에서 순차적으로 배정하여 전송합니다.

##### (10) 테스트 수신 번호 : 입력한 형식을 바탕으로 테스트 발송을 할 수 있습니다. 수신받고자 하는 번호를 입력 후 발송 버튼을 누르면 입력한 번호로 테스트 SMS가 발송됩니다. 실제 발송 전 테스트 발송을 통해 실제 수신형태를 확인하신 후 발송하시기를 권장합니다.

> [참고1]
>
> 쿠폰 아이템을 등록하는 방법은 [Coupon Item](./oper-coupon/#coupon-item)을 참고하시기 바랍니다.
>
> [참고2]
>
> 쿠폰 발송은 SMS 상품을 활성화 해야 사용할 수 있습니다.

#### 7. 쿠폰 추가 발급
쿠폰 타입이 시리얼인 경우 1회 10만 개씩 최대 100만 개까지(초기 발급 개수 포함) 추가로 발급받을 수 있습니다.

![gamebase_coupon_05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_05_240813.png)

#### 8. 쿠폰 통계
쿠폰 발급 상세 정보 화면의 하단에서 SMS 발송 내역을 조회할 수 있으며 발송과 관련된 통계를 조회 및 파일 다운로드를 진행할 수 있습니다.
![gamebase_coupon_06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_06_240813.png)

요청 통계 항목을 통해 실제 발송한 SMS의 발송 통계를 확인할 수 있으며 우측의 다운로드 요청 버튼을 통해 발송 결과에 대한 상세 내역을 다운로드하여 확인할 수 있습니다.
다운로드 요청 후의 상태는 아래와 같습니다.
- **생성 준비 중** : 현재 다운로드 요청이 정상적으로 완료된 상태입니다.
- **생성 중** : 요청된 다운로드 파일을 생성 중입니다.
- **다운로드** : 다운로드 파일이 생성이 완료되었을 경우 다운로드 버튼이 활성화되며 버튼을 클릭하면 발송 상세 내역이 다운로드 됩니다.

## Coupon history

발급한 쿠폰의 사용 내역을 확인할 수 있는 기능을 제공합니다.
검색 조건에 따라 아래와 같은 검색 화면을 제공합니다.

### Properties

#### 쿠폰 코드별 조회

쿠폰 코드를 직접 입력하여 사용여부를 조회할 수 있습니다.
![gamebase_coupon_07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_07_240813.png)

#### 유저 ID별 조회

유저 ID를 통해 해당 유저가 쿠폰을 사용한 이력을 조회할 수 있습니다.
![gamebase_coupon_08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_08_240813.png)

#### 쿠폰명 조회

쿠폰명 및 기타 검색조건을 통해 사용 이력을 조회할 수 있습니다.
![gamebase_coupon_09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_09_240813.png)

1. **쿠폰명**: 쿠폰 발급 메뉴를 통해 발급한 쿠폰을 선택할 수 있습니다.
2. **쿠폰 사용일**: 기간을 설정하여 해당 기간에 사용된 쿠폰만 조회할 수 있는 기능을 제공합니다.

## Coupon Item

쿠폰 코드 사용 시 지급할 쿠폰 아이템을 조회/관리할 수 있습니다.

### Search Coupon item

등록된 쿠폰 아이템 내역을 조회할 수 있습니다.
필터를 통해 아이템 ID/아이템 이름을 통한 검색도 가능합니다.
![gamebase_coupon_10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_10_240813.png)

### Register Coupon item

쿠폰 코드 사용 시 지급할 아이템을 등록합니다.
등록되는 아이템은 단건 입력 또는 파일을 통해 등록할 수 있습니다.

#### 단건 등록

![gamebase_coupon_11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_11_240813.png)

##### 1. 아이템 ID

앱 내에 등록된 아이템 고유 ID를 입력합니다. 쿠폰 코드 사용 시 이곳에 입력된 정보가 실제 서버에 결과 데이터로 전달되므로 아이템을 제공할 수 있는 서버에서 구별할 수 있는 고유 아이템 ID를 입력해야 합니다.
아이템 ID는 최초 등록 후 변경할 수 없으니 주의하여야 합니다.

##### 2. 아이템 이름

등록된 아이템을 구별할 수 있는 아이템 이름을 입력합니다.

#### 파일 업로드

![gamebase_coupon_12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_12_240813.png)
한번에 대량으로 등록하고자 할 때 파일을 이용하여 등록할 수 있습니다.
파일을 이용해서 등록할 경우 한번에 최대 10,000건까지 등록할 수 있으며 템플릿 예시 파일을 다운로드 받은 후 해당 형식에 맞도록 작성해서 업로드를 해주셔야 정상적으로 파일을 이용한 아이템 등록 작업 진행이 가능합니다.

### Update Coupon item

등록한 아이템에 대한 정보를 수정할 수 있으며 해당 아이템을 사용하지 않고자 할 경우 사용하지 않음으로 설정하여 쿠폰 발급시 해당 아이템이 노출되지 않도록 변경할 수 있습니다.

> [참고]
>
> 아이템 ID 정보는 변경할 수 없으므로 아이템 ID가 잘못 되었다면 새로운 아이템 ID로 다시 등록해주셔야 합니다.

![gamebase_coupon_13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_gamebase/ConsoleGuide/Coupon/ko/gamebase_coupon_13_240813.png)

#### 1. 아이템 이름

구별할 수 있는 아이템 이름을 입력합니다.

#### 2. 사용 여부

**사용**상태인 경우에만 쿠폰 등록시 아이템 추가가 가능합니다. 아이템을 쿠폰 등록 화면에서 노출하고 싶지 않은 경우에는 사용 여부를 **사용하지 않음**으로 변경하면 됩니다. 최초 아이템 등록 시에는 항상 **사용**으로 등록됩니다.
