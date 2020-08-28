管理ポートへのGUIアクセス
===========================

(1)	管理用PCから、設定したBIG-IPの管理IPアドレスへ、HTTPSでアクセスします。デフォルトの証明書は、正式に取得した証明書ではないため、以下のような画面が現れますが、「続行する」を選択してください。

.. image:: images/mod2-1-1.png
   :scale: 40%

(2)	ログイン画面が現れますので、以下のデフォルトのIDとPasswordでログインしてください。
ID：admin
Password：admin

.. image:: images/mod2-1-2.png
   :scale: 40%

(3)	バージョン14.0より、デフォルトでBIG-IPのセキュアパスワードポリシーが有効となっています。パスワードポリシーを変更しない限り、v13.0以前のデフォルトパスワードは利用できません。

F5LABでは以下のように設定し、Saveボタンを押します。
- Current Password: admin
- New Password: ilovef5
- Confirm: ilovef5

.. image:: images/mod2-1-3.png
   :scale: 40%

(4)	設定したパスワードでログインし直します。

.. image:: images/mod2-1-4.png
   :scale: 40%

(5)	「Next」ボタンを押します。

.. image:: images/mod2-1-5.png
   :scale: 40%

(6)	ライセンス画面が出ます。「Next」ボタンを押します。

.. image:: images/mod2-1-6.png
   :scale: 40%

~中略~

.. image:: images/mod2-1-7.png
   :scale: 40%

- ライセンスがBIG-IQ License Managerで管理されている場合は、Nextボタンは押せませんので、Resource Provisioningをクリックして下さい。

(7)	プロビジョニング画面がでますので、「APM」にチェックを入れます。「Next」ボタンを押すと再起動の確認がでるので、OKを押します。

.. image:: images/mod2-1-8.png
   :scale: 40%

(8)	SSL証明書の確認がなされますが、デフォルトのまま、「Next」ボタンを押します。

.. image:: images/mod2-1-9.png
   :scale: 40%

(9)	ホスト名、タイムゾーン、Rootのパスワードを設定します。「Next」ボタンを押します。

.. image:: images/mod2-1-10.png
   :scale: 40%

(10)	この後、Standard Network Configurationの「Next」を押すことでウィザード形式にて冗長化も含めた設定が可能ですが、ここではスタンドアローン構成にするため、Advanced Network Configurationの「Finished」ボタンを押します。

.. image:: images/mod2-1-11.png
   :scale: 40%