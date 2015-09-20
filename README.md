# iGALLERIA-API
iGALLERIA / iVet Mediaとの通信用 4D Component

#__目次__

+ <a href="#現行バージョン"><b>現行バージョン</b></a>
+ <a href="#ダウンロード"><b>ダウンロード</b></a>
+ <a href="#%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E6%A7%8B%E6%88%90"><b>ファイル構成</b></a>
 + <a href="#データベース設定"><b>データベース設定</b></a>
+ <a href="#エクスプローラでの表示"><b>エクスプローラでの表示</b></a>
+ <a href="#メソッドエディタでの表示"><b>メソッドエディタでの表示</b></a>
+ <a href="#オブジェクト"><b>オブジェクト</b></a>
 - <a href="#%E6%8E%A5%E7%B6%9A%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>接続オブジェクト</i></b></a>
 - <a href="#%E9%80%81%E4%BF%A1%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>送信オブジェクト</i></b></a>
 - <a href="#%E5%8F%97%E4%BF%A1%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>受信オブジェクト</i></b></a>
     * <a href="#%E5%8C%BB%E7%99%82%E5%B1%9E%E6%80%A7%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>医療属性オブジェクト</i></b></a>
 - <a href="#%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>エラーオブジェクト</i></b></a>
     * <a href="#%E5%9F%BA%E7%A4%8E%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>基礎エラーオブジェクト</i></b></a>
+ <a href="#メソッドリファレンス"><b>メソッドリファレンス</b></a>
 - <a href="#ig_login"><b><i>iG_Login</i></b></a>
 - <a href="#ig_logout"><b><i>iG_Logout</i></b></a>
 - <a href="#ig_upload_media--ivet-media%E7%94%A8"><b><i>iG_Upload_Media</i></b></a><sup> ※ iVet Media用</sup>
 - <a href="#ig_upload_send-ver06%E3%81%BE%E3%81%A7"><font color="gray"><i>iG_Upload_Send</i></font></a><sup> ※ v0.6まで</sup>
 - <a href="#ig_api_gethttpheader"><b><i>iG_API_GetHttpHeader</i></b></a>
 - <a href="#ig_api_getversion"><b><i>iG_API_GetVersion</i></b></a>
 - <a href="#ig_daemon_start"><b><i>iG_Daemon_Start</i></b></a>
 - <a href="#ig_pref_set"><b><i>iG_Pref_Set</i></b></a>
 - <a href="#ig_pref_get"><b><i>iG_Pref_Get</i></b></a>
 - <a href="#ig_folder_list"><b><i>iG_Folder_List</i></b></a>
 - <a href="#ob_new"><b><i>OB_New</i></b></a>
* <a href="#%E4%BB%8A%E5%BE%8C%E5%AE%9F%E8%A3%85%E4%BA%88%E5%AE%9A%E3%81%AE%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89"><b>今後実装予定のメソッド</b></a>
 - <a href="#ig_upload"><b><i>iG_Upload</i></b></a>
 - <a href="#ig_upload_dicom"><b><i>iG_Upload_DICOM</i></b></a>
 - <a href="#ig_item_list"><b><i>iG_Item_List</i></b></a>
 - <a href="#ig_folder_new"><b><i>iG_Folder_New</i></b></a>
 - <a href="#ig_folder_move"><b><i>iG_Folder_Move</i></b></a>
 - <a href="#ig_folder_attributes"><b><i>iG_Folder_Attributes</i></b></a>

#__現行バージョン__
0.7  

* v0.6までのiG_Upload_Sendは無くなりました。
* 今後、アップロード系のコマンドは以下の３つに細分化される予定です。
 + iG_Upload：汎用アップロード
 + iG_Upload_DICOM：カルテAPI向け（DICOMファイル）
 + <a href="#ig_upload_media--ivet-media%E7%94%A8"><b><i>iG_Upload_Media</i></b></a>：カルテAPI向け（DICOM以外のメディアファイル）
* 現行のv0.7では、<a href="#ig_upload_media--ivet-media%E7%94%A8"><b><i>iG_Upload_Media</i></b></a>だけが実装済みです。

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>

#__ダウンロード__

コンポーネントファイル込みのサンプルデータベースと
API接続に対応する機能を実装したiVet Mediaを
tr.igalleria.jpの「iGALLERIA」フォルダにアップロードしてあります。

:arrow_upper_right: <a href="http://tr.igalleria.jp:8080/CATEGORY/000-024/index.html" target=_blank>「iGALLERIA API」フォルダー</a>

0.7の方のZip圧縮ファイルは以下の４つのファイル・フォルダを内包しています：

+ iG_API_v0.7-SampleDB_Media.4dbase（サンプルDB、API Ver 0.7 コンポーネント組み込み済み）
+ iVet-Media+API07.4dbase (東大仕様＋API Ver 0.7 対応)
+ images（アップロードテスト用画像を集めたフォルダ）
+ READ_ME.rtfd（簡単な説明書）


<font color="red"><b>※2015/9/20 PM19時頃 : Ver. 0.7 に更新</b></font>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>

#__ファイル構成__

![FinderScreenSnapz001.jpg](https://solidarrays.qiita.com/files/108b221e-5ea5-2f29-6167-179027d56d9e.jpeg)
__▲ サンプルDB__と__iVet_Media__

ご存知の通りデータベースファイルは実際にはパッケージですので
中を開いてみる事が出来ます．．．．

![FinderScreenSnapz002.jpg](https://solidarrays.qiita.com/files/f80f17b4-b139-adf3-6364-6cffbe953773.jpeg)

__▲ パッケージを開いたところ__

コンポーネントファイルは「__Components__」フォルダに入っているDBファイルです。

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>

##データベース設定

![4DScreenSnapz001.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/aeab378f-a0d3-f580-f95c-800085b132ed.png)
__▲ デザインメニューから「データベース設定...」を選び__
<br>


![4DScreenSnapz002.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/94a0d48e-8ab1-7d1a-4671-b4ccb2d62ec5.png)
__▲「セキュリティ」ページの「コンポーネントの〝On Host Database Events〟メソッドを実行」をONに__
<br>

この設定がなされていないと、iGALLERIA APIコンポーネントは正常に動作しません。
コンポーネントメソッドから「1」のAPIエラーが返ってきて、errorオブジェクトの<font color="maroon"><b>iG_ERR_Msg</b></font>プロパティには<b>「起動時に「On Host Database Event」メソッドが実行されていません。データベース設定が必要です。」</b>というメッセージが返ってきます。
###この設定をOFF → ON にした後は、<b><font color="red">必ず4Dの再起動</font></b>が必要です。
<br>
<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>
<br>

#__エクスプローラでの表示__

![4DScreenSnapz002.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/400b6d43-f310-b2ef-b636-58405441542d.png)
図1:コンポーネントメソッド欄の「iGalleria_API」メソッドグループ


![4DScreenSnapz007.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/06b75d21-9c98-b64c-cf25-c9c48906a6b6.png)
図2：右ペインを「コメント」に切り替えるとメソッド解説が表示

![4DScreenSnapz004.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/de5495f1-13b7-d077-0f54-3e4ddb510ee6.png)
図3：定数ページの一番上にiGalleria_API用の定数グループ

![4DScreenSnapz003.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/06dde066-3e6b-27b8-9f84-1d9827915d05.png)
図4：オブジェクト毎によく使うプロパティが定数として定義済

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>

#__メソッドエディタでの表示__

![4DScreenSnapz001.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/a27444ba-3b8a-cd64-f778-ffa47083b641.png)
図5：タイプアヘッド「ig + TAB」で関連定数・メソッド表示

![4DScreenSnapz006.png](https://qiita-image-store.s3.amazonaws.com/1537/55833/79a06daf-5443-b5c6-6c9f-727d886d7809.png)
図6：APIメソッド名の上にマウスホバーで解説をツールTip表示

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





#__オブジェクト__
当コンポーネントのメソッドでは、引数としてオブジェクトを使う事が多く、また、それらは共通して使われる物が幾つかあります。ここでは、それらの内部プロパティ構成を列挙します。各プロパティの名称は全てカスタム定数を用意してありますので、コードの保守性の観点から出来るだけ定数で指定するようにして下さい。各オブジェクトごとに、決まったプリフィックスを付けてありますので、メソッドエディタに入力する時はタイプアヘッドを適宜活用して頂けます。
各プロパティに渡せるデータの型を示す頭文字は以下の通りです。

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

オブジェクトの特性として、プロパティの型は固定されませんので、実際は何でも渡せますが、当コンポーネントの仕様として下記に示す通りのデータ型を想定して機能が構成されています。プロパティによっては、複数のデータ型の使用を許容しているものもあります。

##__接続オブジェクト__
多くのメソッドで<font color="green"><b>$1</b></font>として渡すオブジェクト。
iGALLERIA/iVet Mediaとの接続に関する情報を渡すために使われます。

|    |プロパティ名|    | 型 | 説明 | デフォルト値 | 値の例 |
|:--:|:------------------------------------------|:--:|:--|:--|:--|:--|
|    |<font color="maroon"><b>iG_CON_Host</b></font>| → | Ｔ |接続先IPアドレス|*なし*|192.168.1.100|
|任意|<font color="maroon"><b>iG_CON_Port</b></font>| → | Ｌ |ポート番号|80||
|  　|<font color="maroon"><b>iG_CON_Name</b></font>| → | Ｔ |ログイン名|*なし*|taro|
|  　|<font color="maroon"><b>iG_CON_Pass</b></font>| → | Ｔ |ログインパスワード|*なし*|hoge|
|任意|<font color="maroon"><b>iG_CON_Timeout</b></font>| → | Ｌ |接続タイムアウト。単位は秒数。|15||
|任意|<font color="maroon"><b>iG_CON_SSL</b></font>| → | Ｂ |SSL通信の使用|False||


##__送信オブジェクト__
多くのメソッドで<font color="green"><b>$2</b></font>として渡すオブジェクト。
iGALLERIA/iVet Mediaへ送信する情報や処理のカスタマイズに関する値を渡すために使われます。

|    |プロパティ名|    | 型 | 説明 | デフォルト値 | 値の例 |
|:--:|:------------------------------------------|:--:|:--|:--|:--|:--|
|    |<font color="maroon"><b>iG_SEND_File</b></font>| → | Ｔ/Ｘ |送信するファイルパス|*無し*||
|任意|<font color="maroon"><b>iG_SEND_To</b></font>| → | Ｌ |アップロード先フォルダー番号。<a href="#ig_upload"><b><i>iG_Upload</i></b></a>のみ使用|*無し*||
|任意|<font color="maroon"><b>iG_SEND_Attr</b></font>| → | Ｏ |アップロードするファイルの属性を集めたオブジェクト。<a href="#ig_upload_media"><b><i>iG_Upload_Media</i></b></a>の場合に限り必須、また<a href="#%E5%8C%BB%E7%99%82%E5%B1%9E%E6%80%A7%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88"><b><i>医療属性</i></b></a>オブジェクトを必ず指定する必要有り。|*無し*||
|任意|<font color="maroon"><b>iG_SEND_AbortOnErr</b></font>| → | Ｔ |エラーが発生したら処理をアボートするか否か|True||
|任意|<font color="maroon"><b>iG_SEND_Callbacks</b></font>| → | Ｌ |コールバックメソッドの名前|*無し*|"OnProgress"|

###__医療属性オブジェクト__
*〜〜（執筆中）〜〜*


##__受信オブジェクト__
*〜〜（執筆中）〜〜*

##__エラーオブジェクト__
*〜〜（執筆中）〜〜*


###__基礎エラーオブジェクト__
*〜〜（執筆中）〜〜*





#__メソッドリファレンス__



##<font color="#428BCA"><b>iG_Login</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Login</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

###__機能__ 
iGalleriaへログインする。

###__引数__

ログイン成功後は、<font color="green"><b>__$1__</b></font>に渡した接続情報オブジェクトはアクティブ状態に変わり、他のAPIコンポーネントメソッドに渡して、同一セッションの処理として実行出来るようになります。
<font color="green"><b>__$2__</b></font>の使用は任意ですが、初期化済みのオブジェクトが必要です。undefinedのままのオブジェクトは渡せません。オブジェクトの初期化に便利なコンポーネントメソッド<a href="#ob_new"><b><i>OB_New</i></b></a> の活用をお勧めします。

　パラメータエラーは、多くの場合、<font color="green"><b>__$1__</b></font>（接続情報）に問題があります。必須の情報が与えられなかった場合などです。オプションである<font color="green"><b>__$2__</b></font>（エラー詳細情報）に渡すオブジェクトが初期化されていなかった場合にもこのエラーが返ってきます。iGalleria APIコンポーネントメソッドで使うオブジェクト型変数は全て<a href="https://solidarrays.qiita.com/Hiroshi_KADOYA/items/91653b90612b2eb5c130#%E5%9E%8B%E5%AE%A3%E8%A8%80%E3%81%A8%E5%88%9D%E6%9C%9F%E5%8C%96" target=_blank> :arrow_upper_right: 初期化済みである必要があります</a>。（参照：コンポーネントメソッド<i><b><a href="#ob_new">OB_New</a></b></i> ）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>コマンドに渡す接続情報を格納したオブジェクト型のデータです。
接続先のiGalleriaが稼働するコンピュータのIPやポート、ログイン情報などをプロパティ値として代入しておきます。<br>
使用可能なプロパティ一覧：

<ul>
<li> <font color="maroon"><b>iG_CON_Host</b></font>：【Ｌ】iGalleriaのIPアドレス
<li> <font color="maroon"><b>iG_CON_Port</b></font>：【Ｌ】iGalleriaのPort番号（省略可能、省略時は80と見なす。）
<li> <font color="maroon"><b>iG_CON_Name</b></font>：【Ｔ】ログイン名
<li> <font color="maroon"><b>iG_CON_Pass</b></font>：【Ｔ】ログインパスワード
<li> <font color="maroon"><b>iG_CON_Timeout</b></font>：【Ｌ】iGalleriaとの通信におけるタイムアウト秒（省略可能、省略時はAPIプリファレンス設定（参考：<a href="#ig_Pref_Get"><b><i>iG_Pref_Get</i></b></a>）の<font color="maroon"><b>iG_PRef_Timeout</b></font>の値が採用されます。初期値は１５秒。）
<li> <font color="maroon"><b>iG_CON_SSL</b></font>：【Ｂ】SSLを使う場合には<b>True</b>（省略可能、省略時は<b>False</b>として扱う）
</ul>
</dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
</dd>

<dt>api_err</dt>
<dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

<ul>
<li> 0：エラー無し（コマンド実行成功）
<li> 1：パラメータエラー
<li> 2：ネットワークエラー
<li> 3：HTTPエラー（iGalleriaロジックエラー）
<li> 4：予期せぬエラー
</ul>
</dd>
</dl>

###__実行例__
<pre>
C_LONGINT ( $err_num )
  // コネクション設定
C_OBJECT($o_con)
OB SET ($o_con; iG_CON_Host; "192.168.0.7")
OB SET ($o_con; iG_CON_Port; 8080)
OB SET ($o_con; iG_CON_Name; "admin")
OB SET ($o_con; iG_CON_Pass; "19813")

  // ログイン
$err_num := <b><i>iG_Login</i></b> ($o_con)

If ($err_num = 0)
   ALERT("ログイン成功！")
End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>

##<font color="#428BCA"><b>iG_Logout</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Logout</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
iGalleriaからログアウトします。
このメソッド実行後は<font color="green"><b>__$1__</b></font>の接続情報オブジェクトのセッションは無効になります。
同じiGalleriaへ同じユーザ権限でアクセスするには、再度<a href="#ig_login"><b><i>iG_Login</i></b></a>でログインする必要があります。

###__引数__
　パラメータエラーは、多くの場合、<font color="green"><b>__$1__</b></font>の接続情報に問題があります。基本的にログインに成功した時のものをそのまま使うのが定石となります。ログインに成功した接続情報オブジェクトには特殊な内部情報が含まれていますので、既にログアウトしてしまったセッションの接続情報オブジェクトは使えません。
　また、オプションである<font color="green"><b>__$2__</b></font>のエラー詳細情報に渡すオブジェクト型変数が初期化されていなかった場合にもパラメータエラーが返ってきます。

 iGalleria APIコンポーネントメソッドで使うオブジェクト型変数は全て初期化済みである必要があります。（参照：コンポーネントメソッド <a href="#ob_new"><b><i>OB_New</i></b></a> ）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
ログインに成功した時の接続情報オブジェクトをそのまま使用することで、そのセッションをログアウトする事が出来ます。<br><br>
</dd>
<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
</dd>
<dt>api_err</dt>
<dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

<ul>
<li> 0：エラー無し（コマンド実行成功）
<li> 1：パラメータエラー
<li> 2：ネットワークエラー
<li> 3：HTTPエラー（iGalleriaロジックエラー）
<li> 4：予期せぬエラー
</ul>

</dd>
</dl>

###__実行例__
<pre>
C_LONGINT ( $err_num )
  // コネクション設定
C_OBJECT($o_con)
OB SET ($o_con; iG_CON_Host; "192.168.0.7")
OB SET ($o_con; iG_CON_Port; 8080)
OB SET ($o_con; iG_CON_Name; "admin")
OB SET ($o_con; iG_CON_Pass; "19813")

  // ログイン
$err_num := <b><i>iG_Login</i></b> ($o_con)

If ($err_num = 0)
   
  // 〜 ここでiGalleriaに対してアップロードなどの処理を実行 〜

  // ログアウト
  $err_num := iG_Logout ($o_con) // ログインで使った接続情報変数を使う

  if ( $err_num )
    ALERT("ログアウトしました")
  End if

End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>


##<font color="#428BCA"><b>iG_Upload_Media</b><sup> ※ iVet Media用</sup></font>
api_err &nbsp; := &nbsp; <I><b>iG_Upload_Media</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; send &nbsp; ; &nbsp; resp &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
|  | $2：send | → | Ｏ |送信データ|
| 任意 | $3：resp | ← | Ｏ |レスポンス|
| 任意 | $4：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
　__iVet Media__専用の__DICOM以外__のアップロードメソッド。
アップロードされた画像やファイルはカルテAPIのWebArea（Media側）から閲覧可能になります。
　アップロード出来るファイルにはサイズ制限があります。デフォルトで<b><font color="red">１００MB</font></b>に設定されています。このサイズを超えるファイルを渡した場合はパラメータエラーになります。この設定値を変更するには <b><i><a href="#ig_pref_set">iG_Pref_Set</a></i></b> を使います。
<pre>このサイズ未満ならアップロードの成功を保証するというわけではありません。
サーバー側のメモリ状況によっては、このサイズ未満でもエラーになる可能性はあります。
あくまで、どれくらい大きなファイルまでアップロードをトライさせても良いかを決めるだけです。</pre>
　アップロードするファイルパスを渡す変数に配列を使う事で複数個のファイルを指定する事が出来ますが、１度に指定出来るファイルの数は最大で__９９９個まで__です。それ以上は、２度、３度とこのメソッドの実行を繰り返して下さい。

###__引数__
　引数１〜４全てオブジェクト型。<font color="green"><b>__$3__</b></font>、<font color="green"><b>__$4__</b></font>は受け取り専用ですが使用は任意です。
　<font color="green"><b>__$3__</b></font>は現在のところ有用な情報は返しませんが、将来の拡張の為に<font color="green"><b>__$3__</b></font>は準備されています。

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iVet Mediaへの接続情報を格納したオブジェクト型のデータです。
ログインに成功した時の接続情報オブジェクトをそのまま使用することで、そのセッションのユーザ権限を引き継いでアップロードする事が出来ます。<font color="red"><b>iVet MediaのカルテAPIで使用するユーザアカウント</b></font>（デフォルトではユーザ名「iVetカルテ」のuser idとpassword）を使用する必要があり、そのアカウントで事前にログインしていなければなりません。<br><br>
</dd>

<dt>send</dt>
<dd><a href="#ig_xxx_xxx"><b>【送信オブジェクト】</b></a>アップロードするファイルパスやアップロード処理に関する様々なパラメータを内包するオブジェクト変数を指定します。<br>
このメソッドでは以下のプロパティを指定します：

<ul>
<li> <font color="maroon"><b>iG_SEND_File</b></font>　：【Ｔ/Ｘ】フルパス<br>
アップロードするファイルをフルパスで指定します。複数のファイルを指定したい場合は、テキスト配列を渡します。
<li> <font color="maroon"><b>iG_SEND_Attr</b></font>　：【Ｏ】属性情報<br>
送信するファイルと対になる属性をまとめたオブジェクト。<br>
下記のプロパティを内部に指定する：
    <ul>
    <li><font color="maroon"><b>iG_SEND_Attr_PatientID</b></font>【Ｔ】患者ID</li>
    <li><font color="maroon"><b>iG_SEND_Attr_AnimalType</b></font>{任意}【Ｔ】動物種別</li>
    <li><font color="maroon"><b>iG_SEND_Attr_Note</b></font>{任意}【Ｔ】備考</li>
    </ul>
複数のファイルをアップロードした場合は、それらの全てに共通する属性として、このオブジェクトで指定した値が書き込まれます。
<li> <font color="maroon"><b>iG_SEND_AbortOnErr</b></font>　：{任意}【Ｂ】エラー発生時の処理続行可否<br>
複数のファイルをアップロードする際、最後のファイル送信以前にエラーが発生した時、残りのファイルのアップロードを続行せずに処理を終了するか否かを指定するプロパティです。<br>
<b>True</b>・・・処理を終了（デフォルト）<br>
<b>False</b>・・・処理を続行<br>
エラー内容に応じて、終了／続行を臨機応変に決定したい場合は、コールバックを使います。<br>
アップロードするファイルが１個の場合は意味を持ちません。

<li> <font color="maroon"><b>iG_SEND_CallBacks</b></font>　：{任意}【Ｔ】コールバックメソッド名<br>
ファイルの送信が１個終わる度に、呼び出されるメソッド。従ってアップロードするファイルを２個以上指定した場合にのみ意味を持つプロパティです。
</ul>

<b> :loudspeaker: <i>アップロード先について</i></b>
<pre>
<i>このメソッドの場合、アップロード先のフォルダーＩＤはコンポーネントが内部的に補いますので、
他のUpload系メソッド（iG_Upload、iG_Upload_Send）のように
iG_SEND_Toプロパティを設定する必要はありません。</i><br><br>
</pre>

</dd>
<dt>resp（任意）</dt>
<dd>v0.7時点では特に有用な情報は返しません。<br>
アップロードの成否についての詳細は<b>error引数</b>（ <font color="green"><b>$4</b></font> ）で受け取る情報を参照して下さい。<br>
<br>
</dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>アップロードの成否に関する詳細な情報が返ってきます。初期化済みオブジェクトを与えておくと、メソッド実行後は下記のようなプロパティ構造になっています：

    <dl>
      <dt>・<font color="maroon"><b>iG_ERR_Count</b></font>：【Ｌ】エラーの発生回数</dt>
            <dd>
            例えば、１０個中３個のファイルのアップロードでエラーが起きたらこのプロパティの値は３です。プロパティ<b>iG_ERR_ArrSeqNo</b>、<b>iG_ERR_ArrObject</b>の要素数と一致します。<br>
            </dd>
      <dt>・<font color="maroon"><b>iG_ERR_ArrSeqNo</b></font>：【Ｘ】エラーが起きたアップロード番号（LONGINT配列）</dt>
            <dd>
            例えば、３番目と５番目のファイルのアップロードにエラーが生じた場合、このプロパティの示す配列の中身は [3,5] となります。
            </dd>
      <dt>・<font color="maroon"><b>iG_ERR_ArrObject</b></font>：【Ｘ】各アップロード毎のエラー情報（オブジェクト配列）</dt>
            <dd>
            エラーの発生した回数分だけこの配列に要素が作られ、各要素の中身は<a href="#ig_xxx_xxx"><b>【基礎エラーオブジェクト】</b></a>です。
            </dd>
      <dt>・<font color="maroon"><b>iG_ERR_Aborted</b></font>：【Ｂ】処理が中断終了されたか否かを示します。</dt>
            <dd>
            エラー、もしくはコールバックメソッドの記述によって、全てのファイルをアップロードする前に処理がアボートされた場合はこのプロパティの値は<b>True</b>です。予定された全てのファイルの送信を行った場合は<b>False</b>です。
<br><br>
<b> :loudspeaker: <i>注意！</i>アボートはエラーの有無とは無関係</b><pre>
送信オブジェクトの<b>iG_SEND_AbortOnErr</b>プロパティの設定やコールバックメソッドの記述内容によっては、
途中で何度エラーが発生しても最後のファイルの送信まで処理を続行させることが可能ですので、
このプロパティの値が<b>False</b>であることが必ずしも全ファイルのアップロード成功を意味するわけではありません。
また、処理の成否に関係なくコールバックメソッドの記述内容によっては処理を途中でアボート出来ますので、
このプロパティの値が<b>True</b>だからといって、必ずしもエラーが起きていた訳でもありません。</pre>
            </dd>
    </dl>

上記以外にもこの<font color="green"><b>$4</b></font>=<b>error</b>引数は、コーディングの単純化を目的にした、プロパティ構成の冗長化が計られています。
例えば、
    <ul>
      <li>メソッドにファイルを１個しか渡さなかった場合
      <li>エラーが起きたら残りのアップロードを諦めて処理をアボートする設定（デフォルト）にしていた場合
    </ul>
このような設定で、エラーが発生した場合、詳細なエラー情報を保持するプロパティ<font color="maroon"><b>iG_ERR_ArrObjects</b></font>の値である配列には要素が１個しか無い事は明白です。そこで、この唯一の配列要素（オブジェクト型）の中身は、自動的に<font color="green"><b>$4</b></font>のトップレベルプロパティとしてもアクセス可能なように複製されています。v0.7時点では４つのプロパティで構成されるこのエラー詳細情報は以下の通りです：

    <ul>
      <li><font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】メソッドの<font color="green"><b>$0</b></font>に返る値と同じです。</dt>
      <li><font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。</dt>
      <li><font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。</dt>
      <li><font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。</dt>
    </ul>

エラーが起きていた場合でも、必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
もちろんエラー無しの場合は、すべてのプロパティの値は数値型なら0、文字型なら空です。
    <br><br>
</dd>

<dt>api_err</dt>
<dd>エラー番号。エラー原因ごとに大まかな分類を示す為の番号です。

<ul>
 <li> <b>0</b>：エラー無し（全てのアップロード成功）
 <li> <b>1</b>：パラメータエラー
 <li> <b>2</b>：ネットワークエラー
 <li> <b>3</b>：HTTPエラー（4Dエラー、iGalleriaロジックエラー含む）
 <li> <b>4</b>：予期せぬエラー
 <li> <b>-1</b>：複数ファイル送信時のエラー（個々のエラー内容は <b>iG_ERR_ArrObject</b>を参照のこと。 ）
</ul>

</dd>
</dl>

###__補足__
このメソッドは、原則的には“オールオアナッシング”な挙動で処理を実行します。結果は「全てのファイルのアップロードに成功するか、１つもアップロードされないか」のいずれかです。この原則の適用から除外されるには、引数<font color="green"><b>$2</b></font>オブジェクトのプロパティ<font color="maroon"><b>iG_SEND_AbortOnErr</b></font>に<b>False</b>を渡してエラー発生時でも残りのアップロードを続行する設定にするか、プロパティ<font color="maroon"><b>iG_SEND_Callbacks</b></font>にメソッド名を渡して、ファイルの送信が１個終わる度にそのメソッドを実行するよう設定し、そのメソッドの<font color="green"><b>$0</b></font>に<b>常にTrueを返す</b>ように記述して処理を最後まで続行させるか、そのいずれかです。
　このように設定した場合、全ファイルアップロードに成功しなくとも、成功したファイルだけiVet Media側に対応するレコードが作成されます。

###__実行例__
<pre>
  // コネクション設定
  〜 省略 （iG_Loginのページを参照）〜

  // ファイルパス取得
  〜 省略 （システム変数Documentに値を得るものとする）〜

  // ログイン
$err_num := iG_Login ($o_con)

If ($err_num = 0)
   
  // 変数定義とオブジェクト初期化
  C_OBJECT ($o_send; $o_resp; $o_err; $o_attr )
  $o_resp := OB_New // 初期化：受信データ用オブジェクト
  $o_err  := OB_New // 初期化：エラー情報用オブジェクト

  // 送信データ
  // - ファイルパス
  OB SET ($o_send; iG_SEND_File; Document)  // アップロードするファイルのフルパス
  // - 属性値データ
  OB SET ($o_attr; iG_SEND_Attr_PatientID; "ABCD12345")  //…………………………………【必須】
  OB SET ($o_attr; iG_SEND_Attr_AnimalType; "猫")  //……………………………………………………{任意}
  OB SET ($o_attr; iG_SEND_Attr_Note; "前肢骨折、手術、山田動物病院、写真") //{任意}
  OB SET ($o_send; iG_SEND_Attr; $o_attr)

  // アップロード
  $err_num := iG_Upload_Media ($o_con; $o_send; $o_resp; $o_err)

  // エラー情報表示
  If ($err_num # 0)
    C_LONGINT( $ErrAPI; $ErrHTTP; $Err4D )
    C_TEXT($ErrMsg; $AlertText)
    $ErrAPI  := OB Get ( $o_err; iG_ERR_Num; Is longint )
    $ErrHTTP := OB Get ( $o_err; iG_ERR_HTTP; Is longint )
    $Err4D   := OB Get ( $o_err; iG_ERR_4D;   Is longint )
    $ErrMsg  := OB Get ( $o_err; iG_ERR_Msg;  Is text )
    $AlertText:=\
      "APIエラーコード："+String($ErrAPI)+"\n"+\
      "HTTPステイタス："+String($ErrHTTP)+"\n"+\
      "4Dエラーコード："+String($Err4D)+"\n"+\
      "エラーメッセージ："+$ErrMsg
    ALERT ($AlertText)
  End if

  // ログアウト
  $err_num := iG_Logout ($o_con)
End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>







##<font color="#999"><b>iG_Upload_Send</b><sup> ※ver.0.6まで</sup></font>
api_err &nbsp; := &nbsp; <I><b>iG_Upload_Send</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; send &nbsp; ; &nbsp; resp &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
|  | $2：send | → | Ｏ |送信データ|
| 任意 | $3：resp | ← | Ｏ |レスポンス|
| 任意 | $4：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
　iGalleriaへファイルをアップロードします。アップロードが成功してもサムネールの生成はログアウトまでペンディングされます。
　アップロード出来るファイルにはサイズ制限があります。デフォルトで<b><font color="red">１００MB</font></b>に設定されています。このサイズを超えるファイルを渡した場合はパラメータエラーになります。この設定値を変更するには <b><i><a href="#ig_pref_set">iG_Pref_Set</a></i></b> を使います。


###__引数__
　引数１〜４全てオブジェクト型。<font color="green"><b>__$3__</b></font>、4は受け取り専用ですが使用は任意です。
　アップロードが成功したファイルをWebページ上で確認する際に必要な情報（folder_code、item_codeなど）を得るためには、<font color="green"><b>__$3__</b></font>へオブジェクトを渡して、レスポンスデータを受け取る必要があります。

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
ログインに成功した時の接続情報オブジェクトをそのまま使用することで、そのセッションのユーザ権限を引き継いでアップロードする事が出来ます。例えば、グループ "ABC" が管理者／スタッフ権限を持っているフォルダへアップロードしたければ、グループ "ABC"に所属するユーザとしてログインしていなければなりません。
</dd>

<dt>send</dt>
<dd><a href="#ig_xxx_xxx"><b>【送信オブジェクト】</b></a>アップロードするファイルやアップロード先のフォルダを指定する為に使うオブジェクト型引数です。
現在のところ、この引数で指定出来るパラメータは、以下のプロパティです：

<ul>
<li> <font color="maroon"><b>iG_SEND_File</b></font>　：【Ｔ】アップロードするファイルのフルパス
<li> <font color="maroon"><b>iG_SEND_To</b></font>　：【Ｌ】アップロード先のフォルダID
</ul>

<b>【自動読み込み機能との連携】</b><br>
OsiriX Dataフォルダや監視フォルダなどの自動取り込み機能のあるフォルダへ直接ファイルをアップロードすると、それぞれの取り込み機能にファイルを渡す事が出来ます。<br>
プロパティ <font color="maroon"><b>iG_SEND_To</b></font> に渡す値はそれぞれ次のようになります：

<ul>
  <li>OsiriX Dataフォルダ：<b>-1</b>（ <font color="maroon"><b>iG_SEND_Dicom</b></font> ）を渡します。</li>
  <li>ユーザ別監視フォルダ：<b>-2</b>（ <font color="maroon"><b>iG_SEND_Media</b></font> ）を渡します。</li>
</ul>

</dd>

<dt>resp（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【受信オブジェクト】</b></a>メソッドがiGALLERIAから取得した情報を受け取るオブジェクトです。<br>
初期化済みオブジェクトを渡す必要があります。<br>
アップロードの通信結果、アップロードしたファイルのDB情報などが得られます。<br>
コマンド実行後、このオブジェクトには下記の２つのプロパティが代入されてきます：

<ul>
 <li> <font color="maroon"><b>iG_RESP_Header</b></font>：【Ｏ】レスポンスのHTTPヘッダー情報です。
 <li> <font color="maroon"><b>iG_RESP_Body</b></font>：【Ｏ】レスポンスのHTTPボディ情報です。
</ul>

両方ともにオブジェクト型のデータですので、それぞれ更に下記のようなプロパティがネストされています。
<br><br>
<b>iG_RESP_Header</b>のプロパティ：

  <ul>
  <li><font color="maroon"><b>iG_RESP_Header_Names</b></font>：【Ｘ】HTTPヘッダ名をまとめたTEXT配列
  <li><font color="maroon"><b>iG_RESP_Header_Values</b></font>：【Ｘ】HTTPヘッダ値をまとめたTEXT配列
  </ul>

　現在のところ、これらのレスポンスHTTPヘッダの中身を直接参照する必要が生じるケースは稀です。iGalleria側のAPI Verやサーバー側で起きたエラーの詳細情報などを取得するのに利用しますが、専用のメソッド（参考：<i><b><a href="#ig_api_gethttpheader">iG_API_GetHttpHeader</a></b></i>）が用意されていますので、そちらを使うケースが殆どでしょう。<br><br>

<b>iG_RESP_Body</b>のプロパティ：

  <ul>
  <li><font color="maroon"><b>iG_RESP_Body_ItemURL</b></font>：【Ｔ】アップロードしたファイルの登録結果を確認出来るWebページのＵＲＬ。該当アイテムの詳細表示ページを指します。<font color="red"><b>※ルート相対パス</b></font>で表現されますので「http://ホスト名」の部分は含まれません。</li>
  <li><font color="maroon"><b>iG_RESP_Body_FolderURL</b></font>：【Ｔ】アップロードしたファイルの登録結果を確認出来るWebページのＵＲＬ。該当アイテムの所属するフォルダ内の一覧表示ページを指します。<font color="red"><b>※ルート相対パス</b></font>で表現されますので「http://ホスト名」の部分は含まれません。</li>
  </ul>

　アップロードが成功していれば上記の情報が得られます。これらのURLを4Dコマンド
<a href="http://doc.4d.com/4Dv14R3/4D/14-R3/OPEN-URL.301-1552470.ja.html" target=_blank><img src="http://www.4d.com/sites/all/themes/dimention/images/common/favicon.gif" valign="top"> <b><font color="green">OPEN URL</font></b></a>
へ渡せば該当アイテムのWebページを開くことも可能です。（実行例参照）
<br><br>
</dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
</dd>

<dt>api_err</dt>
<dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

<ul>
 <li> 0：エラー無し（コマンド実行成功）
 <li> 1：パラメータエラー
 <li> 2：ネットワークエラー
 <li> 3：HTTPエラー（iGalleriaロジックエラー）
 <li> 4：予期せぬエラー
</ul>

</dd>
</dl>

###補足
連続したアップロード処理を行う場合に、出来るだけアップロードを短時間に終わらせることを想定して、このコマンド実行時点では、サムネール作成処理は自動的には発動させていない。ログアウトを実行する時に初めて、サムネール作成デーモンをRESUMEしている。（ <i><b><a href="#ig_logout">iG_Logout</a></b></i> コマンドが内部的に行っています。）
　明示的に任意のタイミングでサムネール作成デーモンをRESUMEさせたい場合は、<i><b><a href="#ig_daemon_start">iG_Daemon_Start</a></b></i> メソッドを使う。

　アップロード出来るファイルにはサイズ制限があります。デフォルトで<b><font color="red">１００MB</font></b>に設定されています。
この設定を変更するには <b><i><a href="#ig_pref_set">iG_Pref_Set</a></i></b> を使います。ただし、このサイズ未満ならアップロードの成功を保証するものではありません。サーバー側のメモリ状況によっては、このサイズ未満でもエラーになる可能性はあります。あくまで、どれくらい大きなファイルまでアップロードをトライさせても良いかを決めるだけです。


###__実行例__
<pre>
  // コネクション設定
  〜 省略 〜

  // ログイン
$err_num := iG_Login ($o_con)

If ($err_num = 0)
   
  // 送信オブジェクト、受信オブジェクト、エラーオブジェクト
  C_OBJECT ($o_send; $o_resp; $o_err )
  $o_send := OB_New // 初期化：送信データ用オブジェクト
  $o_resp := OB_New // 初期化：受信データ用オブジェクト
  $o_err  := OB_New // 初期化：エラー情報用オブジェクト
  // 送信データ
  OB SET ($o_send; iG_SEND_File; Document)  // アップロードするファイルのフルパス
  OB SET ($o_send; iG_SEND_To; 7)  // アップロード先のフォルダーID

  // アップロード
  $err_num := iG_Upload_Send ($o_con; $o_send; $o_resp; $o_err)

  If ($err_num = 0)
    CONFIRM("アップロード成功！ Webページで確認しますか？")
    If ( OK = 1 )
      // respオブジェクトからURLを構築
      C_OBJECT($o_rbody)
      $o_rbody := OB Get ($o_resp; iG_RESP_Body )
      $URL  := OB Get($o_rbody;iG_RESP_Body_ItemURL)
      $HOST := OB Get($o_con;"host";Is text)
      $PORT := OB Get($o_con;"port";Is text)
      If ($PORT#"")
        $PORT := ":" + $PORT
      End if 
      $URL := "http://"+$HOST+$PORT+$URL
      OPEN URL ($URL)  // v14 R2 までは OPEN WEB URL
    End if
    // ログアウト (サムネール作成をサーバーに指示)
    $err_num := iG_Logout ($o_con)
  End if

End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>







##<font color="#428BCA"><b>iG_API_GetHttpHeader</b></font>
value &nbsp; := &nbsp; <I><b>iG_API_GetHttpHeader</b></I> &nbsp; ( &nbsp; headers &nbsp; ; &nbsp; name )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：headers | → | Ｏ |レスポンス ヘッダー|
|  | $2：name | → | Ｔ |ヘッダー名|
|  | $0：value | ← | Ｔ |ヘッダー値|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

　<b><i><a href="#ig_upload_send">iG_Upload</a></i></b> で得たレスポンスに含まれるhttpヘッダー情報から、任意のヘッダー値を抽出します。

###__引数__

<dl>
<dt>headers</dt>
<dd>オブジェクト型の引数です。値の入手元は<b><i><a href="#ig_upload_send">iG_Upload_Send</a></i></b> の第３引数<b>resp</b>で受け取った値（オブジェクト）のプロパティ<font color="maroon"><b>iG_RESP_Header</b></font> の値（オブジェクト）です。
このオブジェクトには、iGalleriaからのレスポンスの全てのHTTPヘッダーが記録されています。<br>　
</dd>

<dt>name</dt>
<dd>抽出したいhttpヘッダー名を指定します。一般的なhttpヘッダー以外に、現在のところ、２つのiGalleriaカスタムヘッダーが定義されています：

  <dl>
  <dt><font color="maroon"><b>iG_RESP_Header_X_Ver</b></font>
  <dd>iGalleria側のAPIバージョンが記されているヘッダー名です。
  <dt><font color="maroon"><b>iG_RESP_Header_X_4DErr</b></font>
  <dd>iGalleria側で起こった4Dエラーの番号とメッセージが記されているヘッダー名です。HTTPステイタス = 500の場合にだけ値が返ってきます。エラーオブジェクトのプロパティ<font color="maroon"><b>iG_ERR_4D</b></font>で得られるメッセージと同一です。
  </dl>

</dd>

<dt>value</dt>
<dd><font color="green"><b>__$2__</b></font>のnameで指定したhttpヘッダーの値が返ってきます。型はTEXT型ですので、数値であるべき情報も文字列として返ってきますので要注意です。<br>　
</dd>
</dl>

###解説
　通信内容を細かく検証したい時に使うユーティリティ メソッドです。現時点では、iGalleria側APIのバージョン番号を調べる時に利用する事が最も多いと思われます。

　アップロードの実行結果でhttp = 400 Bad Request のレスポンスが返ってきたら、APIバージョンの不一致が疑われます。このメソッドでプロパティ <font color="maroon"><b>iG_RESP_Header_X_Ver</b></font> の値を抽出し、<b><i><a href="#ig_api_getversion">iG_API_GetVersion</a></i></b>で得られるコンポーネント側のバージョンと比較して確認する事が出来ます。

　（APIのバージョンはコンポーネントとiGalleria側で一致している必要があり、食い違っていた場合は、コンポーネントメソッド自体がAPIエラーになり、処理は実行出来ません。）

　アップロードの実行結果でhttp = 500 Server Internal Error のレスポンスが返ってきたら、iGALLERIA側でビジネスロジック・アプリケーションロジック上のエラーが疑われます。このメソッドでプロパティ <font color="maroon"><b>iG_RESP_Header_X_4DErr</b></font> の値を取得するとiGALLERIA上で起きたエラーメッセージを確認出来ることがあります。<br>ビジネス／アプリーケーションロジック上のエラーでは、多くの場合「アサーションの失敗」がレポートされます。万一、プログラミングミスによる4Dエラーが起きた場合でも、同様にこのプロパティに4Dエラーの内容がレポートされます。<br>

将来、ＡＰＩ機能の拡張のために様々なカスタムhttpヘッダーが増えていく事になります。
現在利用出来る最新のカスタムヘッダー名の選択肢は、定数グループ __〓 iGalleria API：Response：Header__ から閲覧出来ます。

###__実行例__

<pre>
// ■ アップロード
$err_num := iG_Upload ( $o_con; $o_send; $o_resp; $o_err )

// ■ HTTPエラー判別
If ($err_num >= 3) // 通信確立後のエラーは3以上
    $http := OB Get ($o_err; iG_ERR_HTTP)
    $headers := OB Get ($o_resp; iG_RESP_Header)

    // HTTPステイタス判別
    Case of 
      : ($http = 400)  // 400 Bad Request: APIバージョン不一致かも？
        $VER_Server　:=　iG_API_GetHttpHeader ($headers; iG_RESP_Header_X_Ver)
        $VER_Client　:=　iG_API_GetVersion 
        ALERT ("API Version: "+$VER_Server+" / "+$VER_Client)
    
      : ($http = 500)  // 500 Server Internal Error: サーバ側でエラー発生
        $Server4DError := iG_API_GetHttpHeader ($headers; iG_RESP_Header_X_4DErr)
        ALERT ("iGalleria 4D Error: "+$Server4DError )
    
    End case 
End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>







##<font color="#428BCA"><b>iG_API_GetVersion</b></font>
api_ver &nbsp; := &nbsp; <I><b>iG_API_GetVersion</b></I>

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $0：api_ver | ← | Ｔ |APIコンポーネントVersion|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
iGalleria APIのコンポーネント側のバージョンを返します。

###__引数__

　引数はありません。戻り値にバージョンが返ってきます。

<dl>
  <dt>api_ver</dt>
  <dd>APIのコンポーネント側のバージョン。
iGalleria側のAPIバージョンと一致していないとコマンド実行不可です。
iGalleria側のAPIバージョンの取得は<a href="#ig_api_gethttpheader"><b><i>iG_API_GetHttpHeader</i></b></a>を使う。
  </dd>
</dl>


###__実行例__

<pre>
C_TEXT ( $api_ver )
$api_ver := iG_API_GetVersion
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





##<font color="#428BCA"><b>iG_Daemon_Start</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Daemon_Start</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; daemon &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
| | $1：conn | ⇔ | Ｏ |接続情報|
| | $2：daemon | → | Ｔ |デーモン名|
| 任意 | $3：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
任意のiGalleriaデーモンプロセスをRESUMEさせます。
※現在のところ、サムネール生成デーモン（<font color="maroon"><b>iG_Daemon_Thumbnail</b></font>）のみ対応。

ファイルをアップロードしただけでは、サムネールタスクはキューに登録されるが、タスクの実行はペンディングされています。これは、アップロード受け入れを出来るだけ早く終わらせるための処理スケジュール戦略です。通常は<a href="#ig_logout"><b><i>iG_Logout</i></b></a>が自動的にデーモンをRESUMEさせるので、全てのアップロードが終わればログアウトするだけで、サムネールタスクの処理は始まりますが、何らかの理由で明示的にデーモン起動タイミングをコントロールしたい場合に使います。

###__引数__

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
	ログインに成功した時の接続情報オブジェクトをそのまま使用します。
	<br><br>
</dd>

<dt>daemon</dt>
<dd>RESUMEさせたいデーモンプロセス名。<br>
下記のデーモン名が定数として登録されています。

    <ul>
      <li> <font color="maroon"><b>iG_Daemon_Thumbnail</b></font>：サムネール生成
      <li> <font color="maroon"><b>iG_Daemon_Movie</b></font>：動画エンコーダー
      <li> <font color="maroon"><b>iG_Daemon_OsiriX</b></font>：OsiriXデータ読み込み
      <li> <font color="maroon"><b>iG_Daemon_AutoImport</b></font>：監視フォルダー読み込み
    </ul>

    ※現在のところ実行可能なのは<font color="maroon"><b>iG_Daemon_Thumbnail</b></font>だけです。<br>
ただし、サムネール生成タスクから連携して自動的に生成される動画関連タスクがあるので、<font color="maroon"><b>iG_Daemon_Movie</b></font>も自動的にRESUMEされます。
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

<dt>api_err</dt>
<dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num )
$err_num := iG_Daemon_Start ( $o_con ; iG_Daemon_Thumbnail )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>
　
　
##<font color="#428BCA"><b>iG_Pref_Set</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Pref_Set</b></I> &nbsp; ( &nbsp; new &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：new | → | Ｏ |更新値をまとめたオブジェクト|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

APIプリファレンス値を変更する。
APIプリファレンス値はコンポーネント変数のオブジェクトの幾つかのプロパティとして保持されています。
ホストデータベースからは直接アクセス出来ませんので、専用のメソッド（この<a href="#ig_pref_set"><b><i>iG_PREF_Set</i></b></a>と<a href="#ig_pref_get"><b><i>iG_PREF_Get</i></b></a>）が用意されました。
スコープはインタープロセスです。また、このコマンドの実行結果が有効に保たれるのは<font color="red"><b>4Dが終了するまで</b></font>です。常に任意のプリファレンス値で動作させたい場合は、On Startupなどで希望のプリファレンス値に書き換えるコードを実行する必要があります。


###__引数__

変更したいプリファレンス値を複数一度に更新出来るようにする事と、将来、様々なデータ型のプリファレンス値が追加されても良いように、更新値を指定する引数<font color="green"><b>__$1__</b></font> <b>new</b>はオブジェクトとして渡す仕様にしています。

<dl>
  <dt>new</dt>
  <dd>APIプリファレンス値には以下のプロパティがあります。<br>
それぞれ：以降はデータ型と初期値を表します：
  <dl>
    <dt><font color="maroon"><b>iG_PREF_Timeout</b></font>：【Ｌ】15 ※秒
    <dd>
      iGalleriaと通信するメソッドが、最大何秒までレスポンスを待ち続けるかを決めています。この設定値を超えてレスポンスの無い呼び出しはネットワークエラーになります。
    </dd>
    <dt><font color="maroon"><b>iG_PREF_MaxFileSize</b></font>：【Ｌ】104,857,600 ※bytes
    <dd>
      アップロードするファイルのサイズ上限値をバイト単位で定義します。この設定値を超えたサイズのファイルをアップロードしようとすると、パラメータエラーになります。
    </dd>
    </dl>
  目的のプロパティに希望する値をセットしたオブジェクトを作り、それを<font color="green"><b>__$1__</b></font>へ渡します。<br>
  プロパティ名やデータ型を間違えてしまうと、そのオブジェクトはメソッドに受け入れられません。パラメータエラーとなります。
  <br><br>
  </dd>

  <dt>error（任意）</dt>
  <dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num )
C_OBJECT ( $new )
// タイムアウトのプリファレンス値を変更
OB SET ($new; iG_Pref_Timeout; 30 )// 30秒
$err_num := iG_Pref_Set ( $new )

</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>


##<font color="#428BCA"><b>iG_Pref_Get</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Pref_Get</b></I> &nbsp; ( &nbsp; current &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：current | ← | Ｏ |現在のプリファレンス設定|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
現在のAPIプリファレンス設定を得る。
APIプリファレンス値はコンポーネント変数のオブジェクトの幾つかのプロパティとして保持されています。
ホストデータベースからは直接アクセス出来ませんので、専用のメソッド（この<a href="#ig_pref_get"><b><i>iG_PREF_Get</i></b></a>と<a href="#ig_pref_set"><b><i>iG_PREF_Set</i></b></a>）が用意されました。

###__引数__

<dl>
  <dt>new</dt>
  <dd>現在のプリファレンス設定のコピーを受け取るオブジェクト変数です。<br>
メソッドに渡す前に<a href="https://solidarrays.qiita.com/Hiroshi_KADOYA/items/91653b90612b2eb5c130#%E5%9E%8B%E5%AE%A3%E8%A8%80%E3%81%A8%E5%88%9D%E6%9C%9F%E5%8C%96"><b> :arrow_upper_right: 初期化済み</b></a>である必要があります。<br>
<br>
取得したAPIプリファレンス設定には以下のプロパティがあります。<br>
それぞれコロン（：）以降はデータ型と初期値を表します：
  <dl>
    <dt><font color="maroon"><b>iG_PREF_Timeout</b></font>：【Ｌ】15 ※秒
    <dd>
      iGalleriaと通信するメソッドが、最大何秒までレスポンスを待ち続けるかを決めています。この設定値を超えてレスポンスの無い呼び出しはネットワークエラーになります。
    </dd>
    <dt><font color="maroon"><b>iG_PREF_MaxFileSize</b></font>：【Ｌ】104,857,600 ※bytes
    <dd>
      アップロードするファイルのサイズ上限値をバイト単位で定義します。この設定値を超えたサイズのファイルをアップロードしようとすると、パラメータエラーになります。
    </dd>
    </dl>
  </dd>
  <dt>error（任意）</dt>
  <dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num; $timeout )
C_OBJECT ( $current )
$current := OB_New 
$err_num := iG_Pref_Get ($current)
If ( $err_num = 0 )
  $timeout := OB Get ($current; iG_Pref_Timeout)
End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>



##<font color="#428BCA"><b>iG_Folder_List</b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Folder_List</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; param &nbsp; ; &nbsp; resp &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
|  | $2：param | → | Ｏ |パラメータ|
|  | $3：resp | ← | Ｏ |レスポンス|
| 任意 | $4：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

指定した親フォルダの直下にぶら下がるサブフォルダの情報を返す。
得られる情報は、フォルダ名とフォルダ番号を保持する２つの配列にサブフォルダの数だけ要素が出来ます。

###__引数__

得られた全ての情報は <font color="green"><b>__$3__</b></font>__ : resp__ 引数（オブジェクト）のプロパティとして返されます。

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用します。
    <br><br>
  </dd>

<dt>param</dt>
<dd>メソッドの挙動を指示するために与える値です。オブジェクト型ですので複数のプロパティを渡せますが、今のところ定義済みのプロパティは以下の１つだけです。<br>
    <dl>
      <dt><font color="maroon"><b>iG_Folder_ParentNo</b></font>：【Ｌ】
      <dd>
      親フォルダの番号を指定します。
      </dd>
    </dl>
  </dd>

<dt>resp</dt>
<dd><a href="#ig_xxx_xxx"><b>【受信オブジェクト】</b></a>メソッドがiGALLERIAから取得した情報を受け取るオブジェクトです。<br>
初期化済みオブジェクトを渡す必要があります。<br>
コマンド実行後、このオブジェクトには下記の２つのプロパティが代入されてきます：

<ul>
 <li> <font color="maroon"><b>iG_RESP_Header</b></font>：【Ｏ】レスポンスのHTTPヘッダー情報です。
 <li> <font color="maroon"><b>iG_RESP_Body</b></font>：【Ｏ】レスポンスのHTTPボディ情報です。
</ul>

両方ともにオブジェクト型のデータですので、それぞれ更に下記のようなプロパティがネストされています。
<br><br>
<b>iG_RESP_Header</b>のプロパティ：
  <ul>
  <li><font color="maroon"><b>iG_RESP_Header_Names</b></font>：【Ｘ】HTTPヘッダ名をまとめたTEXT配列
  <li><font color="maroon"><b>iG_RESP_Header_Values</b></font>：【Ｘ】HTTPヘッダ値をまとめたTEXT配列
  </ul>

　現在のところ、これらのレスポンスHTTPヘッダの中身を直接参照する必要が生じるケースは稀です。iGalleria側のAPI Verやサーバー側で起きたエラーの詳細情報などを取得するのに利用しますが、専用のメソッド（参考：<i><b><a href="#ig_api_gethttpheader">iG_API_GetHttpHeader</a></b></i>）が用意されていますので、そちらを使うケースが殆どでしょう。<br><br>


<b>iG_RESP_Body</b>のプロパティ：
    <ul>
      <li><font color="maroon"><b>iG_Folder_NoList</b></font>：【Ｘ】LONGINT配列。サブフォルダー番号を受け取れます。
      </li>
      <li><font color="maroon"><b>iG_Folder_NameList</b></font>：【Ｘ】TEXT配列。サブフォルダー名称を受け取れます。
      </li>
      <li><font color="maroon"><b>iG_Folder_ParentNo</b></font>：【Ｌ】。親フォルダー番号を受け取れます。<br>※<b>引数２：param</b>のプロパティ<font color="maroon"><b>iG_Folder_ParentNo</b></font>で指定した値と同じ。</li>
      <li><font color="maroon"><b>iG_Folder_ParentName</b></font>：【Ｔ】。親フォルダー名を受け取れます。
      </li>
    </ul>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

<dt>api_err</dt>
<dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>

###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





##<font color="#428BCA"><b>OB_New</b></font>
empty_obj &nbsp; := &nbsp; <I><b>OB_New</b></I>

|    | 引数／戻り値 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $0：empty_obj | ← | Ｏ |初期化済オブジェクト|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__
初期化済みのオブジェクトを作成します。

###__引数__／戻り値

<dl>
  <dt>empty_obj</dt>
  <dd>初期化済みオブジェクト。<br>
従って、

<ul><li><a href="http://doc.4d.com/4Dv14R3/4D/14-R3/OB-Is-defined.301-1552293.ja.html" target=_blank><img src="http://www.4d.com/sites/all/themes/dimention/images/common/favicon.gif" valign="top"> <b><font color="green">OB Is defined</font></b></a> は <b>True</b>
<li><a href="http://doc.4d.com/4Dv14R3/4D/14-R3/OB-Is-empty.301-1552302.ja.html" target=_blank><img src="http://www.4d.com/sites/all/themes/dimention/images/common/favicon.gif" valign="bottom"> <b><font color="green">OB Is empty</font></b></a> も <b>True</b></ul>

になる。
このオブジェクトは実体が存在しているので、他のメソッドの引数として値を受け取る用途で使っても正常に機能を果たす事が出来ます。

    <br><br>
  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num; $timeout )
C_OBJECT ( $current )
$current := OB_New 
$err_num := iG_Pref_Get ($current)
If ( $err_num = 0 )
  $timeout := OB Get ($current; iG_Pref_Timeout)
End if
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>
　
　
　
　
　


#__今後実装予定のメソッド__
　





##<font color="#428BCA"><b><i>iG_Upload</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Upload</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; send &nbsp; ; &nbsp; resp &nbsp; ; &nbsp; error &nbsp;)

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
|  | $2：send | → | Ｏ |送信情報|
| 任意 | $3：resp | ← | Ｏ |受信情報|
| 任意 | $4：error | ← | Ｏ |エラー情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>send</dt>
<dd><a href="#ig_xxx_xxx"><b>【送信オブジェクト】</b></a>
（・・・執筆中です・・・）
    <br><br>
  </dd>

<dt>resp</dt>
<dd><a href="#ig_xxx_xxx"><b>【受信オブジェクト】</b></a>
（・・・執筆中です・・・）
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>

###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





##<font color="#428BCA"><b><i>iG_Upload_DICOM</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Upload_DICOM</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; send &nbsp; ; &nbsp; resp &nbsp; ; &nbsp; error &nbsp;)

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
|  | $2：send | → | Ｏ |送信情報|
| 任意 | $3：resp | ← | Ｏ |受信情報|
| 任意 | $4：error | ← | Ｏ |エラー情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>send</dt>
<dd><a href="#ig_xxx_xxx"><b>【送信オブジェクト】</b></a>
（・・・執筆中です・・・）
    <br><br>
  </dd>

<dt>resp</dt>
<dd><a href="#ig_xxx_xxx"><b>【受信オブジェクト】</b></a>
（・・・執筆中です・・・）
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>

###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





##<font color="#428BCA"><b><i>iG_Item_List</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Item_List</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>






##<font color="#428BCA"><b><i>iG_Folder_New</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Folder_New</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>

###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>





##<font color="#428BCA"><b><i>iG_Folder_Move</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Folder_Move</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>

###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>






##<font color="#428BCA"><b><i>iG_Folder_Attributes</i></b></font>
api_err &nbsp; := &nbsp; <I><b>iG_Folder_Attributes</b></I> &nbsp; ( &nbsp; conn &nbsp; ; &nbsp; error &nbsp; )

|    | 引数 |    | 型 | 説明 |
|:--:|:--|:--:|:--|:--|
|  | $1：conn | ⇔ | Ｏ |接続情報|
| 任意 | $2：error | ← | Ｏ |エラー詳細情報|
|  | $0：api_err | ← | Ｌ |エラー番号|

Ｌ＝Longint、Ｔ＝Text、Ｂ＝Boolean、Ｄ＝Date、Ｏ＝Object、Ｐ＝Pointer、Ｘ＝Array

###__機能__

（・・・ *執筆中です* ・・・）

###__引数__

（・・・ *執筆中です* ・・・）

<dl>
<dt>conn</dt>
<dd><a href="#ig_xxx_xxx"><b>【接続オブジェクト】</b></a>iGalleriaへの接続情報を格納したオブジェクト型のデータです。
    ログインに成功した時の接続情報オブジェクトをそのまま使用することで、
    <br><br>
  </dd>

<dt>error（任意）</dt>
<dd><a href="#ig_xxx_xxx"><b>【エラーオブジェクト】</b></a>エラーが起きた場合、詳細なエラー情報が得られる場合があります。
    この引数errorに初期化済みオブジェクトを与えておくと、コマンド実行時にエラーが起きた場合、下記の名前のプロパティが自動的に生成され、相応のエラー情報が返ってきます。

    <ul>
      <li> <font color="maroon"><b>iG_ERR_Num</b></font>：【Ｌ】$0に返る値と同じです。
      <li> <font color="maroon"><b>iG_ERR_Msg</b></font>：【Ｔ】エラー内容を説明するメッセージです。
      <li> <font color="maroon"><b>iG_ERR_4D</b></font>：【Ｌ】4Dのエラーコードです。
      <li> <font color="maroon"><b>iG_ERR_HTTP</b></font>：【Ｌ】httpステータスコードです。
    </ul>

    必ず全てのプロパティに情報が返ってくる訳ではありません。エラーの内容と原因次第です。
    <br><br>
  </dd>

  <dt>api_err</dt>
  <dd>エラー番号。大まかなエラー原因ごとにいくつかのエラーに分類されます。

  <ul>
    <li> 0：エラー無し（コマンド実行成功）
    <li> 1：パラメータエラー
    <li> 2：ネットワークエラー
    <li> 3：HTTPエラー（iGalleriaロジックエラー）
    <li> 4：予期せぬエラー
  </ul>

  </dd>
</dl>


###__実行例__

<pre>
C_LONGINT ( $err_num )
</pre>

<sup><a href="#目次"> :arrow_up: 目次へ戻る</a></sup>
