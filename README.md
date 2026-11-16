# bizcms-local-parts

BIZCMS を、パソコンの中だけ（Docker なし）で動かすときに使う部品の置き場です。
BIZCMS の起動画面が、はじめての1回だけここから取り、指紋（sha256）を確かめてから使います。

## gotrue-v2.197.0

- 中身：[Supabase Auth（GoTrue）](https://github.com/supabase/auth) v2.197.0 を、Windows x64・macOS arm64・macOS x64 向けに組み立てたもの
- 公式は Windows 用と Intel の Mac 用の実行ファイルを配っていないため、元のコードから組み立てました
- Windows 用は、Linux 用の設定（SO_REUSEPORT）を1か所だけ分けました。直しの差は各圧縮ファイルの `BIZCMS-windows.patch` にあります
- 組み立て：Go 1.27.4・`CGO_ENABLED=0`・`-trimpath`・`-ldflags "-s -w"`
- 各圧縮ファイルの中：実行ファイル・`migrations/`（auth の表の SQL。元のコードのまま）・`LICENSE`（MIT。元の倉庫のもの）

| ファイル | sha256 |
|---|---|
| gotrue-v2.197.0-windows-x64.zip | e9b2bc8caa1a164d6077e7016b3ac614f139713c64ca83acccd28c08eb517dd7 |
| gotrue-v2.197.0-darwin-arm64.tar.gz | cff1572cfce22cf42d752bbb8de6f93a9c7e9711b2cf1685a6d9f4781a3e9ced |
| gotrue-v2.197.0-darwin-x64.tar.gz | 7dd1aea3cff2e5ede1db8eb1844f7c16cf5b1e8095195ed3e54f5bbf8ec5b70f |

GoTrue は MIT License です（Copyright の表示は各圧縮ファイルの LICENSE）。
