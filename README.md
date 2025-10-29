変更すべき場所（テンプレートからプロジェクト化する手順）

1) package.json の基本情報
	- "name"
	- "productName"
	- "description"

2) .env のプロジェクト名
	- PROJECT_NAME="starter" → 任意のプロジェクト名に変更
	- これにより `behavior_packs/<PROJECT_NAME>` と `resource_packs/<PROJECT_NAME>` へコピーされます

3) ビヘイビア/リソースパックの manifest.json
	- behavior_packs/starter/manifest.json
		- header.name / header.description
		- header.uuid（新しいUUIDに置き換え）
		- modules[0].uuid（新しいUUIDに置き換え）
		- min_engine_version / dependencies のバージョン確認
	- resource_packs/starter/manifest.json
		- header.name / header.description
		- header.uuid（新しいUUIDに置き換え）
		- modules[0].uuid（新しいUUIDに置き換え）
		- dependencies[].uuid はビヘイビアパックの header.uuid と一致させる


4) Biome 拡張の導入（推奨）
	- エディタで Biome 拡張機能をインストール（例：VS Code の「Biome」）
	- プロジェクト直下の biome.json に従ってフォーマット/リントが有効になります
	- 自動整形を使う場合は「保存時にフォーマット」をオンにしてください

5) pnpm の導入（推奨）
	- Windows PowerShell: `npm i -g pnpm`
	- 依存関係のインストール: `pnpm install`
	- スクリプト例: `pnpm build` / `pnpm build:production` / `pnpm local-deploy` / `pnpm mcaddon`
	- 既存の npm ロックファイルは削除済み（package-lock.json）。pnpm-lock.yaml が生成されます
