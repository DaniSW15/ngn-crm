# My Angular Native app

An Angular app rendering real native views, created from `@ng-native/template`.

```sh
npm start          # Metro; scan the QR code with Expo Go, or press i / a for a simulator
npm run ios        # straight to the iOS simulator
npm run android    # straight to the Android emulator
npm test           # the example test in src/app/app.test.ts, in Node with no simulator
npm run typecheck
```

`src/app/app.ts` is the root component and `src/main.ts` mounts it. Expo Go is enough for development; a
release build or a native module Expo Go does not include needs a development build
(`npx expo run:ios`).

If Metro says `Using development build` and you want Expo Go, press `s`, or start it explicitly
with `npm start -- --go`. Development build mode needs an app already built and installed on the
device. To create one, run `npx expo install expo-dev-client`, then `npx expo run:ios` or
`npx expo run:android`.

Both native app identifiers in `app.json` are set to `com.ngncrm.app`. Set them to your own
reverse-DNS identifiers before publishing.

If iOS reports that `xcrun` is not configured, check `xcode-select -p` and
`xcrun simctl list devices`. With Xcode installed at `/Applications/Xcode.app`, complete its setup:

```sh
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch
xcrun simctl list devices
```

Open Xcode and install an iOS Simulator runtime in Settings > Components if none is available.
If `simctl` still reports a missing CoreSimulator framework after first-launch setup, repair or
reinstall Xcode before retrying `npm run ios`.

The app targets iOS and Android, so `npm run web`, which `create-expo-app` suggests as it finishes,
only says so and exits. Angular Native components can also render in a browser, set up as
https://ng-native.com/packages/web#beside-a-native-app describes.

`AGENTS.md` tells a coding agent how this framework differs from the web Angular it knows
(Claude Code reads it through `CLAUDE.md`). Add your own conventions to it as the app grows.

Docs: https://ng-native.com
