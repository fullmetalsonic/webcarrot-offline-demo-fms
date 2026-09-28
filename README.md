# WebCarrot FMS 오프라인 데모 v1.0.0 | WebCarrot FMS Offline Demo v1.0.0

[데모 실행 · Open demo](https://fullmetalsonic.github.io/webcarrot-offline-demo-fms/) · [오프라인 HTML 다운로드 · Download HTML](https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/latest/download/webcarrot-offline-demo-fms.html) · [소스 브랜치 · Source branch](https://github.com/fullmetalsonic/openpilot/tree/fms-carrot-wip)

## 한국어

이 데모는 **fullmetalsonic/openpilot의 `fms-carrot-wip`** 설정 메뉴를 기기 연결 없이 살펴보고 편집하기 위한 별도 웹페이지입니다. 기준 커밋은 [`0a3d206b`](https://github.com/fullmetalsonic/openpilot/commit/0a3d206b9b89eafe3d502b9ba5e596e89ad7885a)입니다. 공식 `ajouatom/carrot-wip` 데모와 배포·업데이트 주소가 분리되어 있습니다.

1. **설정**에서 원본과 같은 단계별 메뉴 또는 검색으로 파라미터를 찾고 값을 바꿉니다. 차량 선택도 제조사 → 모델 순서로 할 수 있습니다.
2. **도구 → JSON 백업 불러오기**로 콤마 파라미터 백업을 열고, 설정을 수정한 뒤 **백업 JSON 내보내기**로 전달할 수 있습니다.
3. 파라미터 개수가 달라도 가져온 백업의 미지원 키와 수정하지 않은 값·자료형·중첩 구조를 유지합니다. `True`/`False` 문자열로 저장된 이진 설정도 표시하며, 사용자가 직접 바꾼 항목만 새 값으로 기록합니다.
4. 휴대폰 뒤로가기는 차량·값 선택창과 설정 하위 메뉴를 한 단계씩 닫습니다. 최상위 화면에서는 브라우저 기본 뒤로가기가 동작합니다.
5. 인터넷이 연결되면 **도구 → 데모 업데이트**에서 이 FMS 저장소의 정식 Release만 확인합니다. 새 버전이 게시되었을 때만 **업데이트하기**가 나타납니다. 오프라인에서도 현재 데모의 편집 기능은 동작합니다.

현재 정의에는 설정 **184개**가 있습니다. 공식 기준 데모와 비교해 FMS 브랜치의 `PaddleMode` 4번 선택지와 `VEgoStopping` 최소값 1·설명을 반영했습니다. 이 기준 커밋에는 새 운전자 감시 패치가 없으며 기존 `DisableDM` 메뉴를 사용합니다. 차량 목록은 해당 브랜치의 차량 정의와 기존 데모의 목록을 비교해 유지했습니다.

데모는 GitHub Pages에서 실행하거나 단일 HTML을 내려받아 오프라인에서 열 수 있습니다. 기기와 통신하거나 차량에 직접 설정을 적용하지 않습니다. 실제 적용하려면 내보낸 백업을 콤마에서 복원해야 합니다. 온라인 상태의 업데이트 확인은 공개 GitHub Release API만 조회하며, 백업 파일은 GitHub로 전송하지 않습니다.

**동기화 정책:** 이 FMS 데모는 사용자가 요청할 때만 `fms-carrot-wip`과 대조·갱신합니다. 브랜치 변경을 자동으로 가져오거나 주간 배포하지 않습니다.

## English

This separate offline demo follows the settings menu in **`fullmetalsonic/openpilot:fms-carrot-wip`** at commit [`0a3d206b`](https://github.com/fullmetalsonic/openpilot/commit/0a3d206b9b89eafe3d502b9ba5e596e89ad7885a). Its releases and update check are independent from the demo based on the official `ajouatom/carrot-wip` branch.

1. Browse the same nested settings menu or search for a parameter, then edit its value. Vehicle selection follows make → model.
2. Import a Comma parameter backup in **Tools → Import JSON backup**, edit settings, and export a JSON backup to share.
3. Imported unsupported keys and untouched values retain their JSON types and nested structure even when parameter counts differ. Binary `True`/`False` strings display correctly; only explicit edits change the stored value.
4. Phone/browser Back closes the vehicle or value dialog, then moves up through settings groups. At the top level, normal browser Back applies.
5. **Tools → Demo update** checks only this FMS repository’s stable releases. An update button appears when a newer release is available. Current editing remains available offline.

This version embeds **184 settings**. It includes the FMS branch’s `PaddleMode` option 4 and `VEgoStopping` minimum of 1 and its descriptions. That branch commit still uses `DisableDM`; the newer driver monitoring patch is not included.

Open the hosted demo or download its standalone HTML for offline use. It does not connect to a device or directly apply vehicle settings. Restore an exported backup on the Comma device to apply it. The online update check only queries the public GitHub Releases API; backups are not uploaded.

**Sync policy:** This FMS demo is compared with and updated from `fms-carrot-wip` only when the owner requests it. Branch changes are not imported or deployed on a schedule.

## License

The settings and vehicle names reference openpilot and opendbc. Their copyright and MIT notices are retained in [LICENSE](LICENSE), [LICENSE.opendbc](LICENSE.opendbc), and the HTML header. This is an unofficial offline demo.
