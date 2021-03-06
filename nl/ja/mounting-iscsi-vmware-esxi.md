---
copyright:
  years: 1994, 2017
lastupdated: "2017-12-18"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# iSCSI の VMWare ESXi へのマウント

iSCSI の VMWare ESXi へのマウントは、少ないステップで、サーバーおよびストレージ・ノードの詳細のみを使用して行えます。
{:shortdesc}

1. 基本プライベート IP およびユーザー **root** と root のパスワードを使用して vSphere にログインします。
* ウェルカム・ページから、**「構成」**タブをクリックします。
* **「ストレージ・アダプター」**をクリックし、次に**「追加…」**をクリックします。
* **「OK」**をクリックして、ソフトウェア iSCSI アダプターを追加します。
* **「OK」**をクリックして確認します。
* 最新表示の後、新しい iSCSI アダプターがリストされます。
* 下部ペインの**「プロパティー」**をクリックします。
* 「プロパティー」ウィンドウから、最下部の近くにある**「構成」**をクリックし、**「名前」**をサーバーの IQN (許可されたホストの下のストレージ・デバイス・ページにあります) に設定します。
* **「動的ディスカバリー (Dynamic Discovery)」**タブをクリックし、**「追加...」**をクリックします。
* iSCSI サーバーはストレージ・デバイスのターゲット IP になります。その後、**「CHAP..」**ボタンをクリックします。
* **「CHAP を使用 (Use CHAP)」**を選択し、**「親から継承 (Inherit from Parent)」**のチェック・マークを外します。**「ユーザー名」** (許可されたホストの下のストレージ・デバイス・ページにあります) とそのパスワードを入力します。
* 相互 CHAP セクションで**「CHAP を使用しない (Do not use CHAP)」**を選択し、**「OK」**をクリックします。
* 「動的ディスカバリー (Dynamic Discovery)」ウィンドウにデバイスが表示されます。**「閉じる」**をクリックします。
* ストレージ・デバイスの再スキャンを確認します。
* 下部のペインで、デバイスがグレーで「アンマウント」として表示されます。
* デバイス名を右クリックし、**「接続 (attach)」**を選択します。
* 左側の列の**「データストア (Datastore)」**メニューをクリックし、**「ストレージの追加 (add storage)」**をクリックして**「ディスク/LUN (Disc/LUN)」**を選択します。
* 「iqn」を持つデバイスをクリックします。
* 必要なファイル・システム・バージョンを選択し、**「次へ (next)」**をクリックしてウィザードを続行します。
* 完了すると、作成したホストおよび VM の必要に応じて、iSCSI を使用できます。



データ転送サービスの iSCSI デバイスの接続も同じですが、サーバーから IQN を入手する必要があります。ESXi コンソールから以下のステップを実行します。

まず、デバイスを入手する必要があります。

`esxcfg-scsidevs -a | grep iSCSI`

その後、IQN を入手する必要があります (この場合、vmhba33 が iSCSI デバイスです)。

`vmkiscsi-tool -I -l vmhba33`
