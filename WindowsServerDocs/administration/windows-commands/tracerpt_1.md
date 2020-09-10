---
title: tracerpt
description: Tracerpt のリファレンス記事。イベントトレースログ、パフォーマンスモニターによって生成されたログファイル、およびリアルタイムのイベントトレースプロバイダーを解析します。
ms.topic: reference
ms.assetid: cb9eaf86-0ef6-4197-b6c8-9cca8a1d723c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 183f34b7287301c7cf5c58644150fc59dee1576d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628559"
---
# <a name="tracerpt"></a>tracerpt

**Tracerpt**コマンドを使用すると、イベントトレースログ、パフォーマンスモニターによって生成されるログファイル、およびリアルタイムのイベントトレースプロバイダーを解析できます。 ダンプファイル、レポートファイル、およびレポートスキーマが生成されます。

## <a name="syntax"></a>構文

```
tracerpt <[-l] <value [value [...]]>|-rt <session_name [session_name [...]]>> [options]
```

## <a name="options"></a>Options

|              オプションフラグ               |                                                                    説明                                                                    |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
|                   -?                   |                                                         状況依存のヘルプを表示します。                                                          |
|          -config \<filename>           |                                                 コマンドオプションを含む設定ファイルを読み込みます。                                                  |
|                   -y                   |                                                  確認を求めずにすべての質問に対して [はい] を回答します。                                                   |
|            -f \<XML\|HTML>             |                                                                  レポート形式。                                                                   |
|         -/ \<CSV\|EVTX\|XML>          |                                                         ダンプ形式、既定値は XML です。                                                          |
|            -df \<filename>             |                                            Microsoft 固有のカウント/レポートスキーマファイルを作成します。                                            |
|            -int \<filename>            |                                            解釈されたイベント構造体を、指定したファイルにダンプします。                                            |
|                  -rts                  |                        イベントトレースヘッダーに生のタイムスタンプを報告します。 使用できるのは-o、not report、-summary だけです。                         |
|            -tmf \<filename>            |                                                  トレースメッセージ形式の定義ファイルを指定します。                                                  |
|              -tp \<value>              |                            TMF ファイルの検索パスを指定します。 セミコロン (;) で区切られた複数のパスを使用できます。                            |
|              -i \<value>               | プロバイダーイメージのパスを指定します。 一致する PDB は、シンボルサーバーに配置されます。 複数のパスを使用して、セミコロン (;) で区切ることができます。 |
|             -pdb \<value>              |                             シンボルサーバーのパスを指定します。 複数のパスを使用して、セミコロン (;) で区切ることができます。                             |
|                  -gmt                  |                                              WPP ペイロードのタイムスタンプをグリニッジ標準時に変換します。                                               |
|              -rl \<value>              |                                               1 ~ 5 のシステムレポートレベルを定義します。 既定値は 1 です。                                               |
|          -summary [ファイル名]           |                                  概要レポートのテキストファイルを生成します。 指定されていない場合、ファイル名は summary.txt ます。                                   |
|             -o [ファイル名]              |                                      テキスト出力ファイルを生成します。 指定されていない場合、ファイル名は dumpfile.xml ます。                                      |
|           -レポート [ファイル名]           |                                  テキスト出力レポートファイルを生成します。 指定されていない場合、ファイル名は workload.xml ます。                                   |
|                  -lr                   |                        制限の緩い値を指定します。 これは、events スキーマに一致しないイベントに対して最適な作業を行います。                         |
|           -export [ファイル名]           |                                  イベントスキーマエクスポートファイルを生成します。 指定されていない場合、ファイル名は schema. man です。                                   |
|       [-l] \<value [value […]]>        |                                                   処理するイベントトレースログファイルを指定します。                                                    |
| -rt \<session_name [session_name […]]> |                                                リアルタイムイベントトレースセッションのデータソースを指定します。                                                |

## <a name="examples"></a>例

- この例では、 **logfile1** と **logfile2** という2つのイベントログに基づいてレポートを作成し、XML 形式で **logdump.xml** ダンプファイルを作成します。
  ```
  tracerpt logfile1.etl logfile2.etl -o logdump.xml -of XML
  ```
- この例では、イベントログの **ログ**ファイルに基づいてレポートを作成し、ダンプ **logdmp.xml** ファイルを XML 形式で作成して、スキーマに含まれていないイベントを特定し、概要レポートファイル **logdump.txt**を生成し、レポートファイル **logrpt.xml**を生成します。
  ```
  tracerpt logfile.etl -o logdmp.xml -of XML -lr -summary logdmp.txt -report logrpt.xml
  ```
- この例では、 **logfile1** と **logfile2** という2つのイベントログを使用して、既定のファイル名を持つダンプファイルとレポートファイルを生成します。
  ```
  tracerpt logfile1.etl logfile2.etl -o -report
  ```
- この例では、イベントログ **logfile** とパフォーマンスログ **counterfile** を使用して、レポートファイル **logrpt.xml** および Microsoft 固有の XML スキーマファイル **schema.xml**を生成します。
  ```
  tracerpt logfile.etl counterfile.blg -report logrpt.xml -df schema.xml
  ```
- この例では、リアルタイムイベントトレースセッション NT カーネルロガーを読み取り、CSV 形式の **logfile.csv** ダンプファイルを生成します。
  ```
  tracerpt -rt NT Kernel Logger -o logfile.csv -of CSV
  ```
