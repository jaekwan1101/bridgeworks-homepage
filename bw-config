/**
 * ╔══════════════════════════════════════════════════════╗
 * ║   브릿지웍스 설정 파일  — bw-config.js               ║
 * ║   ★ 이 파일의 3개 값만 교체하면 모든 기능 활성화    ║
 * ╚══════════════════════════════════════════════════════╝
 *
 *  STEP 1. 카카오 JavaScript 앱 키 설정
 *    → https://developers.kakao.com 로그인
 *    → 내 애플리케이션 → 앱 키 → JavaScript 키 복사
 *    → KAKAO_JS_KEY 값에 붙여넣기
 *
 *  STEP 2. 카카오 REST API 키 설정 (채널 메시지용, 선택)
 *    → 동일 페이지 → REST API 키 복사
 *    → KAKAO_REST_KEY 값에 붙여넣기
 *
 *  STEP 3. Google Apps Script 웹훅 URL 설정
 *    → https://script.google.com 에서 gas_webhook_v3.gs 붙여넣기
 *    → 배포 → 새 배포 → 웹앱 → 모든 사람 접근 → URL 복사
 *    → GAS_WEBHOOK_URL 값에 붙여넣기
 *
 *  STEP 4. 관리자 페이지 GAS 데이터 URL (STEP 3와 동일)
 *    → GAS_SHEET_URL 값에 동일한 URL 붙여넣기
 */

window.BW_CONFIG = {

  // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  // ★ 여기 3줄만 실제 값으로 교체하세요
  // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  KAKAO_JS_KEY:      '63edb182ab01170c102c663749231293',   // ← 교체 필요
  GAS_WEBHOOK_URL:   'YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL', // ← 교체 필요
  ADMIN_PASSWORD:    'Qkrworhks1@#',                 // ← 관리자 비밀번호

  // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  // 기본 설정 (변경 불필요)
  // ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  COMPANY_NAME:      '브릿지웍스 주식회사',
  ADMIN_EMAIL:       'admin@bridgeworks.co.kr',
  MAX_FILE_SIZE_MB:  10,
  ALLOWED_EXTS:      ['pdf','jpg','jpeg','png','hwp','doc','docx'],
  KAKAO_CHANNEL_ID:  '_YOUR_CHANNEL',    // 카카오 채널 ID (pf.kakao.com/_ID)
  STORE_KEY:         'bw_applications_v2',

  // 테스트 모드 (true = GAS 실제 전송 안 함, 콘솔 로그만)
  TEST_MODE: false,
};

/* ── 카카오 SDK 자동 초기화 ─────────────────────── */
(function initKakaoOnLoad() {
  function tryInit() {
    if (!window.Kakao) return;
    if (Kakao.isInitialized()) return;
    const key = window.BW_CONFIG && window.BW_CONFIG.KAKAO_JS_KEY;
    if (!key || key.startsWith('YOUR_')) {
      console.warn('[BW_CONFIG] 카카오 JS 키 미설정 — KAKAO_JS_KEY를 교체하세요');
      return;
    }
    try {
      Kakao.init(key);
      console.log('[BW_CONFIG] ✅ 카카오 SDK 초기화 완료');
    } catch(e) {
      console.error('[BW_CONFIG] 카카오 SDK 초기화 실패:', e);
    }
  }
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', tryInit);
  } else {
    tryInit();
  }
})();
