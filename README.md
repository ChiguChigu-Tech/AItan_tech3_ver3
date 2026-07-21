# AI単（AItan）

英単語学習と英語論文読解を支援する、Streamlitベースの学習アプリケーションです。  
2024年度のHack U 東京電機大学で、チーム「Tech3!」として企画・開発しました。

## 概要

AI単は、英単語の検索・復習・可視化に加えて、英語論文PDFから学習対象となる語句を抽出し、意味や出現頻度とともに保存できるアプリケーションです。

単語を個別に調べるだけでなく、論文読解中に出会った専門用語を学習データへ取り込み、その後の復習につなげることを目指しました。

## 主な機能

### 単語検索

英単語の意味、発音記号、例文などを取得し、学習データへ登録します。

### 単語テスト

登録した単語を使ったクイズを通じて、学習内容を復習します。

### Voca鍋

学習した単語を視覚的に表示し、学習状況を直感的に確認します。

### 論文解析

英語論文のPDFをアップロードし、本文から名詞・動詞・形容詞・副詞や複合語を抽出します。

- PDF本文の抽出
- spaCyによる品詞解析・レンマ化
- 単語および複合語の抽出
- 出現頻度の集計
- Google翻訳またはOpenAI APIによる日本語訳
- 分野タグの付与
- 学習用CSVへの保存・ダウンロード

### 学習データ・単語傾向

登録済みの単語、学習状況、分野ごとの傾向などを確認します。

## 使用技術

- Python
- Streamlit
- pandas
- spaCy
- OpenAI API
- Google Cloud Text-to-Speech API
- deep-translator
- unstructured

## セットアップ

### 1. リポジトリの取得

```bash
git clone https://github.com/ChiguChigu-Tech/AItan_tech3_ver3.git
cd AItan_tech3_ver3
```

### 2. 依存ライブラリのインストール

```bash
pip install -r requirements.txt
```

### 3. spaCy英語モデルのインストール

```bash
python -m spacy download en_core_web_sm
```

### 4. 認証情報の設定

OpenAI APIを利用する機能では、Streamlit Secretsなどを使ってAPIキーを設定してください。

```toml
# .streamlit/secrets.toml
[ApiKey]
OPENAI_API_KEY = "your-api-key"
```

Google Cloud Text-to-Speech APIを利用する場合は、Google Cloudの認証情報をローカル環境に設定する必要があります。

> APIキー、サービスアカウント鍵、秘密情報をGitへコミットしないでください。

### 5. アプリケーションの起動

```bash
streamlit run main.py
```

## ディレクトリ構成

```text
.
├── database/              # 単語・論文学習データ
├── images/                # アプリ内画像
├── my_learning/           # 学習データ表示
├── my_setting/            # ユーザー設定
├── paper_analysis/        # 英語論文からの語句抽出・翻訳
├── pb_chart/              # Voca鍋・可視化
├── pronunciation/         # 意味・発音・音声生成
├── trend_analysis/        # 単語傾向の分析
├── word_quiz/             # 単語テスト
├── word_search/           # 単語検索
├── main.py                # Streamlitエントリーポイント
├── requirements.txt
└── utils.py
```

## プロジェクト資料

- [最終発表資料](https://drive.google.com/file/d/1MYzj8bV4TWYHQt4dyR0IWOVtqDRm5uXA/view?usp=sharing)
- [個人の担当範囲](./MY_CONTRIBUTIONS.md)

## 開発体制

本プロジェクトはチーム開発です。各メンバーが機能ごとに実装を担当し、`main.py`から各ページを呼び出す構成で統合しました。

このリポジトリにおける関元也の担当範囲は、[`MY_CONTRIBUTIONS.md`](./MY_CONTRIBUTIONS.md)に記載しています。

## 注意事項

- 本リポジトリはハッカソン期間中に開発したプロトタイプです。
- 外部APIの仕様変更などにより、そのままでは動作しない機能がある可能性があります。
- 自動翻訳や生成AIの出力には誤りが含まれる可能性があるため、論文の原文や信頼できる資料と照合してください。
- アップロードする論文PDFの著作権、利用条件、機密性を確認したうえで利用してください。

## Status

Hack U 東京電機大学 2024で開発した成果物です。現在はポートフォリオとして公開しています。
