---
title: CLR ETW プロバイダー
description: 2 つの共通言語ランタイム (CLR) Windows イベント トレーシング (ETW) プロバイダー (ランタイム プロバイダーとランダウン プロバイダー) の詳細を確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: f537a2e0557f1b0434d1f303d74f9cd48f157edc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283875"
---
# <a name="clr-etw-providers"></a>CLR ETW プロバイダー

共通言語ランタイム (CLR: Common Language Runtime) には、ランタイム プロバイダーとランダウン プロバイダーという 2 つのプロバイダーがあります。  
  
 ランタイム プロバイダーは、有効になっているキーワードに応じてイベントを発生させます (キーワードとはイベントのカテゴリです)。 たとえば、ローダー イベントを収集するには `LoaderKeyword` キーワードを有効にします。  
  
 Windows イベント トレーシング (ETW: Event Tracing for Windows) イベントのログは、.etl 拡張子を持つファイルに記録されます。これは、必要に応じてコンマ区切り値 (.csv) ファイル内で後処理できます。 .etl ファイルを .csv ファイルに変換する方法の詳細については、「[.NET Framework のログ記録の制御](controlling-logging.md)」を参照してください。  
  
## <a name="the-runtime-provider"></a>ランタイム プロバイダー  

 ランタイム プロバイダーは、メインの CLR ETW プロバイダーです。  
  
 CLR ランタイム プロバイダーの GUID は e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 です。  
  
 一般に利用可能なツールを使用して CLR ETW イベントを記録および表示する方法の例については、「[.NET Framework のログ記録の制御](controlling-logging.md)」を参照してください。  
  
 `LoaderKeyword` などのキーワードを使用する以外にも、発生頻度が高いイベントを記録するためのキーワードを有効にしなければならない場合があります。 `StartEnumerationKeyword` キーワードと `EndEnumerationKeyword` キーワードはこれらのイベントを有効にします。概要については、「[CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」(CLR ETW のキーワードおよびレベル) を参照してください。  
  
## <a name="the-rundown-provider"></a>ランダウン プロバイダー  

 ランダウン プロバイダーは、一部の特殊な用途で有効にする必要があります。 ただし、大半のユーザーにとっては、ランタイム プロバイダーで十分です。  
  
 CLR ランダウン プロバイダーの GUID は A669021C-C450-4609-A035-5AF59AF4DF18 です。  
  
 通常は、プロセスが開始される前に ETW のログを有効にし、プロセスの終了後にログを無効にしますが、 プロセスの実行中に ETW ログを有効にする場合もあります。その場合は、そのプロセスについて追加の情報が必要です。 たとえば、シンボルを解決するには、ログを有効にする前に既に読み込まれていたメソッドのメソッド イベントを記録する必要があります。  
  
 `DCStart` イベントと `DCEnd` イベントは、データの収集が開始されたときと停止されたときのプロセスの状態をキャプチャします  (状態とは、既に Just-In-Time (JIT) コンパイルされているメソッド、既に読み込まれているアセンブリなど、高レベルの情報を指します。)この 2 つのイベントを使用すると、そのプロセスで既に行われたことに関する情報 (どのメソッドが JIT コンパイルされたかなど) を取得できます。  
  
 ランダウン プロバイダーで発生するイベントは、名前に `DC`、`DCStart`、`DCEnd`、または `DCInit` を含むイベントだけです。 また、これらのイベントはランダウン プロバイダーでしか発生しません。  
  
 ランダウン プロバイダーでは、イベント キーワード フィルターのほかに、`StartRundownKeyword` と `EndRundownKeyword` というキーワードによるターゲット フィルターもサポートされています。  
  
### <a name="start-rundown"></a>開始ランダウン  

 開始ランダウンは、`StartRundownKeyword` キーワードを使用してランダウン プロバイダーのイベントの記録を有効にした場合にトリガーされます。 開始ランダウンがトリガーされると、`DCStart` イベントが発生して、システムの状態がキャプチャされます。 列挙の開始前には `DCStartInit` イベントが発生します。 列挙の終了時には `DCStartComplete` イベントが発生して、データの収集が正常に終了したことがコントローラーに通知されます。  
  
### <a name="end-rundown"></a>終了ランダウン  

 終了ランダウンは、`EndRundownKeyword` キーワードを使用してランダウン プロバイダーのイベントの記録を有効にした場合にトリガーされます。 終了ランダウンでは、実行中のプロセスのプロファイリングが停止され、 `DCEnd` イベントにより、プロファイリングが停止されたときのシステムの状態がキャプチャされます。  
  
 列挙の開始前には `DCEndInit` イベントが発生します。 列挙の終了時には `DCEndComplete` イベントが発生して、データの収集が正常に終了したことがコンシューマーに通知されます。 開始ランダウンと終了ランダウンは、主にマネージド シンボルの解決のために使用されます。 開始ランダウンは、プロファイリング セッションが開始される前に既に Just-In-Time コンパイル (JIT コンパイル) されていたメソッドのアドレス範囲の情報を提供します。 終了ランダウンは、プロファイリングを停止するときに JIT コンパイルされていたすべてのメソッドのアドレス範囲の情報を提供します。  
  
 終了ランダウンは、プロファイリング セッションが停止されると自動的に発生するわけではありません。 ツールでマネージド シンボルを解決する必要がある場合は、プロファイリングを停止する直前に、`EndRundownKeyword` キーワードを有効にして CLR ランダウン プロバイダー セッションを明示的に呼び出す必要があります。  
  
 マネージド シンボルを解決するためのメソッドのアドレス範囲の情報は、開始ランダウンと終了ランダウンのどちらでも取得できますが、`EndRundownKeyword` キーワード (`DCEnd` イベント) ではなく `StartRundownKeyword` キーワード (`DCStart` イベント) を使用することをお勧めします。 `StartRundownKeyword` を使用すると、プロファイリング セッションの間にランダウンが発生するため、プロファイリング対象のシナリオに影響を与える可能性があります。  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>ランタイム プロバイダーとランダウン プロバイダーによる ETW データの収集  

 次の例は、マネージド プロセスのシンボルを、プロセスの開始または終了がプロファイリング期間の範囲内かどうかに関係なく最小限の影響で解決できるようにするための CLR ランダウン プロバイダーの使用方法を示しています。  
  
1. CLR ランタイム プロバイダーを使用して ETW のログの記録を有効にします。  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     ログは、clr1.etl ファイルに保存されます。  
  
2. プロセスの実行中にプロファイリングを停止するには、ランダウン プロバイダーを開始して `DCEnd` イベントをキャプチャします。  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     これにより、`DCEnd` イベントの収集を有効にして、ランダウン セッションを開始できます。 すべてのイベントが収集されるまでには 30 ～ 60 秒かかります。 ログは、clr1.et2 ファイルに保存されます。  
  
3. すべての ETW プロファイリングを停止します。  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. プロファイルをマージして 1 つのログ ファイルを作成します。  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     merged.etl ファイルには、ランタイム プロバイダー セッションとランダウン プロバイダー セッションのイベントが含まれます。  
  
 ツールを使用して、ユーザーがプロファイリングの停止を要求したときに直ちにプロファイリングを停止する代わりに手順 2. と 3. (ランダウン セッションを開始してからプロファイリングを終了する) が実行されるようにすることも、 手順 4. もツールで実行できます。  
  
## <a name="see-also"></a>関連項目

- [共通言語ランタイムの ETW イベント](etw-events-in-the-common-language-runtime.md)
