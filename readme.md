# pic-build-sample
PICのコード(アセンブラ)をmakeでビルドするサンプルコード．  
書き込みもコマンドライン上で可能　　

# 動作確認をした環境
- MPLAB 5.00
- Windows10(11)
Windowsで使用する場合はBash上でないと動かないので注意

# requirement
- MPLAB
- jre
  - ipecmd用
- make
- Bash
  - Windowsの場合，コマンドプロンプトやPowershellでは動かないので注意
  - Git Bash利用を推奨

# 構成
```
.
│   .gitignore
│   Makefile
│   readme.md
│
├───asm
│       main.asm
│
└───build
        MAIN.hex
        オブジェクトファイルなど
```
asmディレクトリとbuildディレクトリはgitignoreしています．

# make使い方

ソースコードをビルドする  
```
make
```

オブジェクトファイルを消去  
```
make clean
```

picに書き込み  
```
make write
```

オブジェクトファイルの削除，ソースコードのビルド，PICに書き込みを全部やる  
```
make all
```