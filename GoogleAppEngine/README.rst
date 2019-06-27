
====================================================================================
Google App Engine でよく使うコマンド
====================================================================================

・ PCに登録されているアカウント表示

gcloud auth list

・ PCに登録されているAppEngineの設定表示

gcloud config list

・ アカウント追加

gcloud auth login

・ プロジェクト変更

gcloud config set project xxxx

・ Google App Engine に反映させる

gcloud app deploy -v 01