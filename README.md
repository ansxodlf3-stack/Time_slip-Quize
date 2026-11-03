# 타임슬립 S2 — GitHub 전용 APK 빌드 프로젝트

PC나 Android IDE 없이 **GitHub Actions가 APK를 빌드**하도록 구성한 Android 프로젝트입니다.

## 패드에서 사용하는 순서

1. GitHub에서 새 저장소(repository)를 만듭니다. 예: `timeslip-s2`
2. 이 ZIP의 **압축을 푼 파일/폴더 내용**을 저장소에 업로드합니다. ZIP 파일 자체를 저장소에 넣는 것이 아닙니다.
3. `main` 브랜치에 커밋하면 `.github/workflows/build-apk.yml`이 자동 실행됩니다.
4. GitHub 저장소의 **Actions → Build TimeSlip APK**를 엽니다.
5. 실행된 workflow의 결과에서 **timeslip-s2-apk** artifact를 다운로드합니다.
6. 다운로드한 ZIP 안의 `app-debug.apk`를 패드에서 설치합니다.

### GitHub 모바일 앱을 쓰는 경우
GitHub 모바일에서는 저장소 생성은 가능하지만 파일 업로드는 모바일 브라우저를 이용하는 편이 쉽습니다. 브라우저에서 GitHub 저장소 → **Add file → Upload files**로 프로젝트 파일을 올리세요.

## 수동 빌드
Actions 화면에서 **Build TimeSlip APK → Run workflow**를 눌러도 됩니다.

## Release APK
`v1.0.0` 같은 태그를 push하면 `release-apk.yml`이 GitHub Release를 만들고 APK를 Release asset으로 붙입니다.

## 프로젝트 구조

```text
TimeSlipHistory/
├── .github/workflows/
│   ├── build-apk.yml
│   └── release-apk.yml
├── app/
│   ├── src/main/assets/index.html
│   ├── src/main/java/com/timeslip/history/MainActivity.java
│   ├── src/main/AndroidManifest.xml
│   └── build.gradle
├── build.gradle
└── settings.gradle
```

> 이 프로젝트의 APK는 GitHub Actions에서 생성되는 debug APK입니다. 개인 테스트/설치용으로 사용할 수 있습니다. Play 스토어 배포용 release 서명은 별도의 signing 설정이 필요합니다.
