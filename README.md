# Initialize React Native project

Install expo-cli and eas globally `npm install -g expo-cli eas-cli`
run `npm install`

Change the project name inside (no space e.g. my-app-name)
- `package.json -> "name"`
- `app.json -> "name"`
- `app.json -> "slug"`

change Android package URI
```json
{
  "expo": {
    "android": {
      "package": "com.<teamname>.<myapp>" // com.eliag.expoinit
    },
  }
}
```


Install the debugger (go to the root of the project)
```bash
wget https://github.com/jhen0409/react-native-debugger/releases/download/v0.12.1/rn-debugger-windows-x64.zip
mkdir ./scripts/rndebugger && unzip ./rn-debugger-windows-x64.zip -d ./scripts/rndebugger/
rm ./rn-debugger-windows-x64.zip
```

## If WSL
### symlink adb in windows to wsl
```bash
mkdir -p ~/android/cdmline-tools/platform-tools
sudo ln -s <path-to-adb.exe> ~/android/cmdline-tools/platform-tools/adb
```

### Add adb to ANDROID_HOME variable
e.g. for zsh in .zshrc
```bash
export ANDROID_HOME=~/android
export PATH=$ANDROID_HOME/cmdline-tools/tools/bin/:$PATH
export PATH=$ANDROID_HOME/platform-tools/:$PATH           // This one is needed, other its optionals
export PATH=$ANDROID_HOME/emulator/:$PATH
```

### Forward port from wsl to windows using wslbridge.ps1 script
```bash
pwsh.exe -c \"start-process pwsh -Verb runas -ArgumentList '-File C:/scripts/wslbridge.ps1'\"
```

## Using debugger
Open debugger before start running `npm run debugger`

if you get some error on debugger run `npm explain react-devtools-core` and check that all version is 4.14.
if not:
- run `rm -rf node_modules/react-native/node_modules/react-devtools-core node_modules/react-devtools-core package-lock.json` to cleanup your project
- run `npm explain react-devtools-core` if error your project is clean
- run `npm install`
- run `npm explain react-devtools-core` you have to get something like that:
```
react-devtools-core@4.14.0
node_modules/react-devtools-core
  react-devtools-core@"4.14.0" from react-native@0.70.5
  node_modules/react-native
    react-native@"0.70.5" from the root project
```

## Run app
Connect phone via USB and run `npm run dev`

With terminal in focus press 'm' to open menu in Expo Go then select `Debug Remote JS` and it will automatically connect to debugger
