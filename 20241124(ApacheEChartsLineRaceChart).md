# Apache ECharts Line Race Chart 옵션 설명

Apache ECharts를 사용하여 Line Race 차트를 구성할 때, 다양한 옵션을 활용할 수 있습니다. 각 옵션은 차트의 시각적 효과, 데이터 표시 방식, 상호작용을 조정하는 데 중요한 역할을 합니다. 여기서는 주요 옵션과 그 적용 방법을 자세히 설명하겠습니다.

## 1. 기본 Line Race Chart 옵션

### 1.1 기본 구성 요소
- **title**: 차트 제목을 설정합니다. 위치, 스타일 등을 지정할 수 있습니다.
  ```javascript
  title: {
      text: '전체 및 년도별 월별 에너지 사용량 평균',
      left: 'center' // 제목 위치 설정
  }
  ```
  - `text`: 차트 제목의 내용입니다.
  - `left`, `top`, `right`, `bottom`: 제목의 위치를 설정합니다.

- **tooltip**: 데이터 포인트 위에 마우스를 올렸을 때 정보가 표시됩니다.
  ```javascript
  tooltip: {
      trigger: 'axis', // 축을 기준으로 툴팁 표시
      formatter: '{b0}: {c0}' // 툴팁 표시 형식 지정
  }
  ```
  - `trigger`: 'axis'로 설정하면 축을 기준으로 툴팁이 표시되며, 'item'으로 설정하면 각 데이터 포인트별로 표시됩니다.
  - `formatter`: 툴팁의 포맷을 지정할 수 있습니다.

- **legend**: 시리즈의 범례를 설정합니다. 범례는 차트의 상단이나 하단에 표시되며, 시리즈를 구분하는 데 사용됩니다.
  ```javascript
  legend: {
      top: '10%',
      data: ['전체 월별 평균', '년도별 평균']
  }
  ```
  - `top`, `left`, `bottom`, `right`: 범례의 위치를 설정합니다.
  - `data`: 범례에 표시할 시리즈의 이름입니다.

### 1.2 축 구성
- **xAxis**와 **yAxis**: x축과 y축을 정의합니다.
  ```javascript
  xAxis: {
      type: 'category',
      data: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월']
  },
  yAxis: {
      type: 'value'
  }
  ```
  - `type`: 'category'는 카테고리 축을 의미하며, 'value'는 수치 축을 의미합니다.
  - `data`: x축의 각 라벨을 설정합니다.

### 1.3 시리즈 구성
- **series**: 데이터 시리즈를 정의합니다.
  ```javascript
  series: [
      {
          name: '전체 월별 평균',
          type: 'line',
          data: avgUsageValues,
          showSymbol: false, // 각 데이터 포인트에 심볼을 표시하지 않음
          emphasis: {
              focus: 'series' // 강조 모드: 해당 시리즈 강조
          },
          animationDuration: 5000, // 애니메이션 지속 시간 (밀리초)
          animationEasing: 'linear' // 애니메이션 가속화 방식
      }
  ]
  ```
  - `name`: 시리즈의 이름으로, 범례와 툴팁에 표시됩니다.
  - `type`: 시리즈의 타입으로 'line'을 지정해 라인 차트를 만듭니다.
  - `data`: 시리즈에 표시할 데이터를 지정합니다.
  - `showSymbol`: 데이터 포인트에 심볼을 표시할지 여부를 설정합니다. 일반적으로 `false`로 설정해 데이터가 많은 경우 그래프가 깔끔하게 보이도록 합니다.
  - `emphasis`: 특정 시리즈에 마우스를 올렸을 때 강조하는 효과를 설정합니다.
  - `animationDuration` 및 `animationEasing`: 애니메이션의 속도와 가속 방식을 설정합니다. `linear`는 선형 애니메이션을 의미합니다.

## 2. Line Race Chart 추가 옵션 및 사용 방법

### 2.1 `connectNulls`
- **설명**: 데이터에 `null` 값이 있을 때, 선을 끊지 않고 연결할지 여부를 설정합니다.
  ```javascript
  connectNulls: true // 데이터에 null 값이 있어도 선을 연결
  ```

### 2.2 `label` 옵션
- **설명**: 각 데이터 포인트에 라벨을 표시할 수 있습니다.
  ```javascript
  label: {
      show: true, // 라벨 표시 여부
      position: 'top', // 라벨의 위치 (예: 'top', 'left', 'right', 'bottom')
      formatter: '{c}' // 표시할 라벨의 형식 (예: 데이터 값)
  }
  ```
  - `show`: 라벨 표시 여부를 설정합니다.
  - `position`: 라벨이 표시될 위치를 설정합니다.
  - `formatter`: 라벨의 표시 형식을 지정합니다.

### 2.3 `endLabel` 옵션
- **설명**: 각 라인의 끝에 라벨을 추가하여 현재 값이나 상태를 표시할 수 있습니다.
  ```javascript
  endLabel: {
      show: true,
      formatter: function (params) {
          return params.value[0] + ': ' + params.value[1];
      }
  }
  ```
  - `show`: 끝 라벨 표시 여부를 설정합니다.
  - `formatter`: 표시 형식을 정의합니다. 이 예제에서는 시리즈 이름과 해당 값이 라벨로 표시됩니다.

### 2.4 `animation` 관련 옵션
- **설명**: 차트의 애니메이션 설정을 통해 더 매력적인 시각화를 구현할 수 있습니다.
  - `animationDuration`: 애니메이션이 시작하고 끝날 때까지의 지속 시간을 설정합니다.
  - `animationEasing`: 애니메이션의 진행 방식을 설정합니다. 'linear', 'cubicIn', 'cubicOut' 등의 값을 사용하여 애니메이션의 형태를 정의할 수 있습니다.

## 3. 사용 방법 요약
1. **기본 구성 요소 설정**: `title`, `tooltip`, `legend`를 통해 차트 제목, 툴팁, 범례를 설정합니다.
2. **축 설정**: `xAxis`와 `yAxis`를 통해 축의 유형과 데이터를 정의합니다.
3. **데이터 시리즈 추가**: `series` 옵션을 통해 라인 차트를 구성하고, 데이터 포인트, 라벨, 애니메이션 등을 설정합니다.
4. **상호작용과 시각적 효과 강화**: `connectNulls`, `label`, `endLabel`, `animation` 등의 옵션을 활용하여 차트를 더욱 매력적으로 만들 수 있습니다.

이러한 옵션들을 적절히 조합하여 사용하면, 데이터에 대한 인사이트를 효과적으로 전달할 수 있는 멋진 Line Race Chart를 만들 수 있습니다. ECharts 공식 문서도 참고하여 각 옵션을 상세히 조정해 보세요!

