# Apache ECharts Gauge Chart 옵션 설명

Apache ECharts를 사용하여 게이지(Gauge) 차트를 구성할 때, 다양한 옵션을 활용할 수 있습니다. 각 옵션은 차트의 시각적 효과, 데이터 표시 방식, 상호작용을 조정하는 데 중요한 역할을 합니다. 여기서는 주요 옵션과 그 적용 방법을 자세히 설명하겠습니다.

## 1. 기본 Gauge Chart 옵션

### 1.1 기본 구성 요소
- **title**: 차트 제목을 설정합니다. 위치, 스타일 등을 지정할 수 있습니다.
  ```javascript
  title: {
      text: '에너지 사용량 현황',
      left: 'center' // 제목 위치 설정
  }
  ```
  - `text`: 차트 제목의 내용입니다.
  - `left`, `top`, `right`, `bottom`: 제목의 위치를 설정합니다.

- **tooltip**: 데이터 포인트 위에 마우스를 올렸을 때 정보가 표시됩니다.
  ```javascript
  tooltip: {
      formatter: '{a} <br/>{b}: {c} kW' // 툴팁 표시 형식 지정
  }
  ```
  - `formatter`: 툴팁의 포맷을 지정할 수 있습니다. `{a}`는 시리즈 이름, `{b}`는 항목 이름, `{c}`는 값입니다.

### 1.2 시리즈 구성
- **series**: 데이터 시리즈를 정의합니다.
  ```javascript
  series: [
      {
          name: '에너지 사용량',
          type: 'gauge',
          startAngle: 200,
          endAngle: -20,
          min: 0,
          max: 10,
          radius: '100%',
          axisLine: {
              lineStyle: {
                  width: 10,
                  color: [[0.3, '#67e0e3'], [0.7, '#37a2da'], [1, '#fd666d']]
              }
          },
          pointer: {
              length: '60%',
              width: 4
          },
          detail: {
              fontSize: 16,
              formatter: '{value} kW'
          },
          data: [
              { value: 2.4, name: '전력' }
          ]
      }
  ]
  ```
  - `name`: 시리즈의 이름으로, 범례와 툴팁에 표시됩니다.
  - `type`: 시리즈의 타입으로 'gauge'를 지정해 게이지 차트를 만듭니다.
  - `startAngle`과 `endAngle`: 게이지의 시작 및 끝 각도를 설정합니다.
  - `min`과 `max`: 게이지의 최소 및 최대 값을 설정합니다.
  - `axisLine`: 게이지의 축 라인을 설정합니다.
    - `lineStyle`: 축 라인의 스타일을 정의합니다.
    - `color`: 게이지 값에 따라 다른 색상을 설정할 수 있습니다.
  - `pointer`: 게이지의 포인터(바늘)의 길이와 두께를 설정합니다.
  - `detail`: 게이지의 중앙에 표시되는 값의 스타일을 설정합니다.
  - `data`: 게이지에 표시할 데이터를 설정합니다.

## 2. Gauge Chart 추가 옵션 및 사용 방법

### 2.1 `axisTick`
- **설명**: 축 눈금을 설정합니다.
  ```javascript
  axisTick: {
      splitNumber: 5, // 눈금 사이의 분할 수
      length: 8, // 눈금 길이
      lineStyle: {
          color: 'auto'
      }
  }
  ```
  - `splitNumber`: 눈금 사이의 분할 수를 설정합니다.
  - `length`: 눈금의 길이를 설정합니다.
  - `lineStyle`: 눈금의 스타일을 정의합니다.

### 2.2 `axisLabel`
- **설명**: 축 레이블을 설정합니다.
  ```javascript
  axisLabel: {
      fontSize: 12,
      distance: 10,
      formatter: '{value} kW' // 레이블의 형식을 지정
  }
  ```
  - `fontSize`: 레이블의 폰트 크기를 설정합니다.
  - `distance`: 레이블과 축 간의 거리를 설정합니다.
  - `formatter`: 레이블의 형식을 지정합니다.

### 2.3 `splitLine`
- **설명**: 게이지의 주요 분할선을 설정합니다.
  ```javascript
  splitLine: {
      length: 20, // 주요 분할선의 길이
      lineStyle: {
          width: 3,
          color: 'auto'
      }
  }
  ```
  - `length`: 주요 분할선의 길이를 설정합니다.
  - `lineStyle`: 분할선의 스타일을 정의합니다.

### 2.4 `progress`
- **설명**: 게이지의 진행 상태를 시각적으로 나타냅니다.
  ```javascript
  progress: {
      show: true, // 진행 상태 표시 여부
      width: 10 // 진행 상태 바의 너비
  }
  ```
  - `show`: 진행 상태 표시 여부를 설정합니다.
  - `width`: 진행 상태 바의 너비를 설정합니다.

## 3. 사용 방법 요약
1. **기본 구성 요소 설정**: `title`, `tooltip`을 통해 차트 제목과 툴팁을 설정합니다.
2. **시리즈 설정**: `series` 옵션을 통해 게이지 차트를 구성하고, 데이터 포인트, 축, 진행 상태 등을 설정합니다.
3. **축 설정 및 기타 설정**: `axisTick`, `axisLabel`, `splitLine`을 통해 축과 눈금, 레이블 등을 정의합니다.
4. **상호작용과 시각적 효과 강화**: `progress` 등의 옵션을 활용하여 게이지 차트를 더욱 매력적으로 만들 수 있습니다.

이러한 옵션들을 적절히 조합하여 사용하면, 데이터에 대한 인사이트를 효과적으로 전달할 수 있는 멋진 Gauge Chart를 만들 수 있습니다. ECharts 공식 문서도 참고하여 각 옵션을 상세히 조정해 보세요!

