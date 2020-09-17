SSLサーバ証明書の設定
===========================

BIG-IPが持つデフォルトのサーバ証明書は、正式な認証局で取得したものではないため、クライアントPCのWebブラウザでVirtual Serverへアクセスすると、以下のような警告が出ます（IEの場合の例）。

.. image:: images/mod4-3-1.png
   :scale: 40%

以降、正式な認証局(例：Verisign，CyberTrust等)にて署名されたサーバ証明書をインポートして利用するまでの手順を示します。

**F5LABで利用するサーバ証明書**

| 一般的には、BIG-IPのGUIでCSRと秘密鍵を生成し、CSRを認証局（例：ベリサイン等）に送付します。そのCSRに対して、認証局が署名を行うことでサーバ証明書が完成します。そのサーバ証明書を返送してもらい、インポートします。
| 本ガイドでは簡易的に、秘密鍵ファイルとサーバ証明書の両方がすでに存在しているものとし、両方をインポートする手順とします。
| リモートデスクトップ接続したPCのデスクトップ上にある、以下のフォルダを開いてください。

.. image:: images/mod4-3-2.png
   :scale: 40%

このフォルダ内の以下2つのファイルを使用します。

| ①	秘密鍵ファイル：		abcCompany-key.pem
| ②	サーバ証明書ファイル：	abcCompany-cert.pem

**秘密鍵とサーバ証明書のインポート**

(1)サーバの秘密鍵をインポートします。 「System」 → 「Certificate Management」 → 「Traffic Certificate Management」 →「SSL Certificate List」で表示された画面右上の「Import」ボタンを押します。

.. image:: images/mod4-3-3.png
   :scale: 40%

(2)Keyを選択します。

.. image:: images/mod4-3-4.png
   :scale: 40%

(3)以下のように設定します。

.. image:: images/mod4-3-5.png
   :scale: 40%

- Key Name: Key の名称（任意）を指定
- Key Source: Key ファイルを Upload

(4)以下の状態になります。

.. image:: images/mod4-3-6.png
   :scale: 40%

(5)次にサーバ証明書をインポートします。インポートした秘密鍵をクリックすると、以下の画面が現れます。「Import」ボタンを押します。

.. image:: images/mod4-3-7.png
   :scale: 40%

(6)以下のように設定（インポート）します。

.. image:: images/mod4-3-8.png
   :scale: 40%

- Certificate Source: サーバ証明書ファイルを Upload

(7)サーバ証明書がインポートされた状態です。

.. image:: images/mod4-3-9.png
   :scale: 40%


**Client SSL Profileの生成とVSへの割当て**

(1)Client SSL Profileの生成
| 「Local Traffic」 → 「Profile」 → 「SSL」 → 「Client」で表示された画面右上の「Create」ボタンを押すと、以下の画面が表示されます。以下のように設定します。

.. image:: images/mod4-3-10.png
   :scale: 40%

- Name: 名前（任意）を指定
- Certificate Key Chain: 右のチェックボックスをチェックし、Addボタンをクリック

(2)「Add」ボタンを押すと以下のような設定画面が表示されるので、「abcCompany」を設定します。

.. image:: images/mod4-3-11.png
   :scale: 40%

- Certificate: abcCompany を選択
- Key: abcCompany を選択
- Addをクリック

(3)以下のように表示されます。
| Certificate Key Chain に、（2）で選択したCertificate , Key が選択されていることを確認し、Finishdをクリックします。

.. image:: images/mod4-3-12.png
   :scale: 40%

~（略）~

.. image:: images/mod4-3-13.png
   :scale: 40%

(4)作成した設定が登録されていることを確認。

.. image:: images/mod4-3-14.png
   :scale: 40%

(5)Virtual ServerへのClient SSL Profileの割当て
| 「Local Traffic」 → 「Virtual Servers」 を選択し、SSL-VPN接続用に設定したVirtual Serverをクリックすると、以下の画面が表示されます。

.. image:: images/mod4-3-15.png
   :scale: 40%

~（略）~

.. image:: images/mod4-3-16.png
   :scale: 40%

- 既存の Client SSL Profile をAvailable に移動し、作成した Client SSL Profile を Selected に移動します。
- 画面最下部の Update をクリックします。
