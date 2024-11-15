### ❓리액트에서 성능 최적화를 위한 방법들을 설명해주세요.

리액트에서 성능 최적화 방법은 메모이제이션을 활용한 방법이 있습니다.
‘React.memo’, ‘useMemo’, ‘useCallback’과 리액트 내장 함수를 활용하여 성능 최적화를 할 수 있습니다. 또한 ‘React.lazy’ 와 ‘Suspense’를 사용하여 코드 스플리팅을 할수도 있습니다.

##### 💡예상 꼬리 질문

### ❓React.memo, useMemo, useCallback의 차이점

‘React.memo’는 컴포넌트 자체를 메모이제이션하여 재랜더링을 방지합니다. 일반적으로 값이 자주 변하지 않지만 컴포넌트가 리렌더링 되면 성능에 영향을 주는 상황에서 유용합니다.
‘useMemo’는 특정 값의 계산한 결과를 메모이제이션 합니다. 값이 복잡하거나 시간이 오래 걸리는 연산이 경우 해당 값이 변경되지 않는 한 이전 계산 결과를 재사용합니다.
‘‘useCallback’은 함수 자체를 메모이제이션합니다. 자식 컴포넌트에 함수를 props를 전달할 때 불필요한 리렌더링을 방지할 수 있습니다.
`useMemo`와 `useCallback`은 단순한 값을 계산하는 데 사용하는 것 보다는 비용이 높은 연산이거나, 자식 컴포넌트 리렌더링이 성능에 중요한 경우에만 사용하는 것이 좋습니다.

### ❓브라우저 렌더링 파이프라인에 대해서 설명해주세요.

먼저 HTML DOM 트리를 생성합니다. 그다음에 CSSOM 트리를 생성하게 됩니다.
그 후 HTML DOM 트리와 CSSOM 트리를 결합하여 렌더 트리를 생성하게 됩니다.
그리고 레이아웃 크기를 계산하여 페인팅 됩니다. 마지막으로 컴포지팅 단계로 레이어를 결합하여 최종 화면을 구성합니다. 이러한 과정이 순차적으로 이루어지며 웹페이지가 최종적으로 사용자에게 렌더링이 됩니다.

### ❓인터넷 창에서 url을 입력하면 무슨 일이 일어나는지 설명해주세요.

첫번째로 DNS 조회가 일어납니다. 브라우저에 캐시된 DNS 기록을 먼저 확인 후 없으면 DNS 서버에 요청하여 url에 해당하는 IP 주소를 얻습니다. 그후에 TCP 연결을 수립합니다. 세번째는 HTTP 요청입니다. TCP 연결이 수립되면 브라우저는 HTTP 또는 HTTPS 요청을 보냅니다. 이 과정에서 브라우저와 서버가 암호화된 연결을 설정하기 위해 보안 인증서를 교환하고 암호화 키를 협상합니다. 네번째로 서버의 응답이 옵니다. 리소스를 브라우저에게 응답으로 보냅니다. 마지막으로 받은 리소스를 바탕으로 브라우저가 렌더링 됩니다.