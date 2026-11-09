# WebCarrot FMS 오프라인 데모 v1.0.5 | WebCarrot FMS Offline Demo v1.0.5

[데모 실행 · Open demo](https://fullmetalsonic.github.io/webcarrot-offline-demo-fms/) · [오프라인 HTML 다운로드 · Download HTML](https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/latest/download/webcarrot-offline-demo-fms.html) · [소스 브랜치 · Source branch](https://github.com/fullmetalsonic/openpilot/tree/fms-carrot-wip)

## 한국어

이 데모는 **fullmetalsonic/openpilot의 `fms-carrot-wip`** 설정 메뉴를 기기 연결 없이 살펴보고 편집하기 위한 별도 웹페이지입니다. 기준 커밋은 [`201d3fe`](https://github.com/fullmetalsonic/openpilot/commit/201d3fe45b55389846d0ccfec9524574e74d19c2)입니다. 공식 `ajouatom/carrot-wip` 데모와 배포·업데이트 주소가 분리되어 있습니다.

1. **설정**에서 원본과 같은 단계별 메뉴 또는 검색으로 파라미터를 찾고 값을 바꿉니다. 차량 선택도 제조사 → 모델 순서로 할 수 있습니다.
2. **도구 → JSON 백업 불러오기**로 콤마 파라미터 백업을 열고, 설정을 수정한 뒤 **백업 JSON 내보내기**로 전달할 수 있습니다.
3. 파라미터 개수가 달라도 가져온 백업의 미지원 키와 수정하지 않은 값·자료형·중첩 구조를 유지합니다. `True`/`False` 문자열로 저장된 이진 설정도 표시하며, 사용자가 직접 바꾼 항목만 새 값으로 기록합니다.
4. 휴대폰 뒤로가기는 차량·값 선택창과 설정 하위 메뉴를 한 단계씩 닫습니다. 최상위 화면에서는 브라우저 기본 뒤로가기가 동작합니다.
5. 인터넷이 연결되면 **도구 → 데모 업데이트**에서 이 FMS 저장소의 정식 Release만 확인합니다. 새 버전이 게시되었을 때만 **업데이트하기**가 나타납니다. 오프라인에서도 현재 데모의 편집 기능은 동작합니다.

현재 정의에는 설정 **205개**가 있습니다. v1.0.4 이후 무게중심 비율, 깜빡이·모델 표시, ATC 우회전 차선 변경 거리, Comma Pedal 등 12개가 추가됐습니다. 차량 목록에는 원본에 있는 테슬라 모델 3·Y의 네 이름을 추가했습니다. FMS의 패들 모드 4, `DisableDM` 0/1/2, `VEgoStopping` 최솟값 1을 포함합니다.

숫자 버튼을 길게 누르면 반복 조절하고, 설정별 배율은 브라우저에 저장됩니다. 선택지는 누르면 바로 적용되고, 다른 값에서 기본값으로 바꿀 때는 확인을 요청합니다. 차량별 숨김과 차간 거리 단계는 차량명과 백업의 지원 정보를 사용합니다. 기존 백업에서 건드리지 않은 큰 숫자는 자릿수를 그대로 내보냅니다. 불러온 백업과 편집값은 탭별로 보관되어 새로고침 후 복원되며, 파일을 읽는 중에는 편집과 내보내기를 잠시 막습니다. 업데이트 시 기존 보관본과 충돌하면 사용할 백업을 직접 선택할 수 있습니다. ATC 거리의 기존 값 `1`은 파일에 유지되며, FMS 기기에서 복원할 때 250m로 처리됩니다.

데모는 GitHub Pages에서 실행하거나 단일 HTML을 내려받아 오프라인에서 열 수 있습니다. 기기와 통신하거나 차량에 직접 설정을 적용하지 않습니다. 실제 적용하려면 내보낸 백업을 콤마에서 복원해야 합니다. 온라인 상태의 업데이트 확인은 공개 GitHub Release API만 조회하며, 백업 파일은 GitHub로 전송하지 않습니다.

**동기화 정책:** 이 FMS 데모는 사용자가 요청할 때만 `fms-carrot-wip`과 대조·갱신합니다. 브랜치 변경을 자동으로 가져오거나 주간 배포하지 않습니다.

v1.0.1에서는 검색 결과를 갱신할 때 입력창을 유지해 휴대폰 한글 조합이 끊기던 문제를 수정했습니다. 일부 모바일 브라우저에서 겹쳐 보이던 검색어 삭제 버튼도 하나로 정리했습니다.

v1.0.2에서는 “스티어링”과 “스테어링” 검색어도 원본 메뉴의 “조향” 및 `Steer` 설정을 찾도록 했습니다.

v1.0.3에서는 최신 FMS 설정 정의와 상세·검색 전용·차량별 표시 규칙을 반영하고, Pages에서 업데이트할 때 설정을 보관하는 경로를 수정했습니다.

v1.0.4에서는 숫자 설정 98개의 조절을 원본 웹캐럿과 맞췄습니다. 배율은 `x1 → x2 → x5 → x10 → x50 → x100`으로 순환하며, 선택한 숫자만큼 정확히 증가·감소합니다. 범위가 좁은 설정 5개에도 배율 버튼을 표시하고, 직접 입력은 배율과 별개로 범위 안의 정수를 1 단위로 입력할 수 있습니다. FMS 설정 정의와 차량 목록은 그대로입니다.

## English

This separate offline demo follows the settings menu in **`fullmetalsonic/openpilot:fms-carrot-wip`** at commit [`201d3fe`](https://github.com/fullmetalsonic/openpilot/commit/201d3fe45b55389846d0ccfec9524574e74d19c2). Its releases and update check are independent from the demo based on the official `ajouatom/carrot-wip` branch.

1. Browse the same nested settings menu or search for a parameter, then edit its value. Vehicle selection follows make → model.
2. Import a Comma parameter backup in **Tools → Import JSON backup**, edit settings, and export a JSON backup to share.
3. Imported unsupported keys and untouched values retain their JSON types and nested structure even when parameter counts differ. Binary `True`/`False` strings display correctly; only explicit edits change the stored value.
4. Phone/browser Back closes the vehicle or value dialog, then moves up through settings groups. At the top level, normal browser Back applies.
5. **Tools → Demo update** checks only this FMS repository’s stable releases. An update button appears when a newer release is available. Current editing remains available offline.

This version embeds **205 settings**, including 12 additions since v1.0.4. Four Tesla Model 3 and Model Y names were restored from the FMS vehicle definitions. The FMS schema includes paddle mode 4, `DisableDM` 0/1/2, and a minimum of 1 for `VEgoStopping`.

Numeric buttons repeat when held, and the browser remembers each setting's increment. Choices apply immediately, while a reset to a different default asks for confirmation. Vehicle visibility and gap levels use the selected vehicle and backed-up capability. Export preserves the digits of untouched large numbers. Each tab stores its imported backup and edits for restoration after reload. Editing and export pause while a file is loading. If an update conflicts with an existing tab backup, a recovery panel asks which backup to use. The legacy ATC distance value `1` stays in the file and is interpreted as 250 m when restored on FMS.

Open the hosted demo or download its standalone HTML for offline use. It does not connect to a device or directly apply vehicle settings. Restore an exported backup on the Comma device to apply it. The online update check only queries the public GitHub Releases API; backups are not uploaded.

**Sync policy:** This FMS demo is compared with and updated from `fms-carrot-wip` only when the owner requests it. Branch changes are not imported or deployed on a schedule.

v1.0.1 keeps the search input mounted while results update, so Korean IME composition is not interrupted. It also removes the duplicate clear button shown by some mobile browsers.

v1.0.2 also maps Korean “스티어링/스테어링” searches to the source menu’s “조향” and `Steer` entries.

v1.0.3 updates the FMS definitions and detail, search-only, and vehicle-brand visibility rules. It also fixes the hosted update path that carries the current settings into the new Pages version.

v1.0.4 matches the source WebCarrot controls for all 98 numeric settings. Increments cycle through `x1 → x2 → x5 → x10 → x50 → x100`, and each selected number is the actual increment or decrement. Five narrow-range settings regain their increment buttons. Direct entry accepts in-range integers at a step of 1, independently of the selected increment. FMS definitions and the vehicle catalog are unchanged.

## License

The settings and vehicle names reference openpilot and opendbc. Their copyright and MIT notices are retained in [LICENSE](LICENSE), [LICENSE.opendbc](LICENSE.opendbc), and the HTML header. This is an unofficial offline demo.
