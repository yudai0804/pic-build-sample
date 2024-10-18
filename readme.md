# pic-makefile-template
PICのコード(アセンブリ)をmakeでビルドするサンプルコード．  
書き込みもコマンドライン上で可能  

# 構成
```
.
│   .gitignore
│   LICENSE
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

# Environment
動作確認済み環境
- Windows10、11、Debian12、Ubuntu22
- MPLAB 5.35
- jre 1.8.0_431
- make

## Setup(Windows)
### make、Git Bashをインストール
make、Git Bashは各自好きな方法でインストールしてください  

scoopの場合

scoopをインストール(インストール済みであれば不要)  
PowerShellで以下のコマンドを実行
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```
make git bashをインストール
```
scoop install git make
```

### MPLABをインストール  
MPLAB 5.35のインストーラーをリンクから取得、実行
https://www.microchip.com/en-us/tools-resources/archives/mplab-ecosystem

### Oracle JREをインストール
https://www.java.com/ja/download/windows_manual.jsp

## Linux
### MPLABをインストール
インストールリンク
https://www.microchip.com/en-us/tools-resources/archives/mplab-ecosystem
```
dpkg --add-architecture i386
apt-get update && apt-get install -y libc6:i386 libx11-6:i386 libxext6:i386 libstdc++6:i386 libexpat1:i386
```
```
tar -xvf MPLABX-v5.35-linux-installer.tar
sudo ./MPLABX-v5.35-linux-installer.sh
```
参考:https://developerhelp.microchip.com/xwiki/bin/view/software-tools/ides/x/archive/linux/

### Oracle JREをインストール
https://www.java.com/ja/download/
```
tar zxvf jre-8u73-linux-x64.tar.gz
```
73の部分はダウンロードしたもののバージョンに合わせてください。

環境変数の追加

Makefileで`IPECMD_JAVA`という環境変数を使用するため、ダウンロードしたOracle JREを環境変数に設定してください。  
例(.bashrc)
```
export IPECMD_JAVA="$HOME/jre1.8.0_431/bin/java"
```
```
source ~/.bashrc
```

## 注意事項
- MPLABのバージョンは必ず5.35以下にしてください。5.35よりはPICのアセンブラ(MPASM)が付属していないからです。特に理由がなければ、5.35を使用することを強く推奨します。
- Javaの実行環境(JRE)にはOracle JREとOpenJRE(OpenJDK)の2種類がありますが、前者でしかIPECMDは動作しません。
- パスが異なる場合は、必要に応じてMakefileや環境変数を変更してください。

# License
MIT License