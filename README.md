# whisper-wasm

## Getting started
### generate the private key
```
./whisper-wasm -generatekey | awk '{ print $4; }' | tee ./testdata/key.txt
```
### start bootnode
```
./whisper-wasm -idfile ./testdata/key01.txt -ip 0.0.0.0:30303 -sympass wwww -standalone
```

### start second node
```
./whisper-wasm -idfile ./testdata/key02.txt -boot enode://98bb759bfcdcbea96c9f50592ef410d169a66d4f18f11c7ab85b26b39ee510929f2a3fca545ad81fb6ef02f91ae8e75b784ee132d6aacea0dcb283c08adb6724@127.0.0.1:30303 -ip 0.0.0.0:30304 -topic 5a4ea131 -sympass wwww
```

## Wasm library compile
```
GOARCH=wasm GOOS=js go build -o ./wasm/test.wasm main.go

cd wasm

go run server.go
```