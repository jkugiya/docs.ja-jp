---
description: '詳細情報: <source> の <listeners> の <add> 要素'
title: <source> の <listeners> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: cb2145738b81574397a8de13f68d0d4e572f20cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639836"
---
# <a name="add-element-for-listeners-for-source"></a>\<source> の \<listeners> の \<add> 要素

トレース ソースの `Listeners` コレクションにリスナーを追加します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>構文  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|必須属性です。ただし、`sharedListeners` コレクション内のリスナーを参照する場合は、名前だけで参照することができます (「[例](#example)」を参照)。<br /><br /> リスナーの種類を指定します。 「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定された要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定されたクラスのコンストラクターに渡される文字列。 クラスに文字列を受け取るコンストラクターがない場合は、<xref:System.Configuration.ConfigurationException> がスローされます。|  
|`name`|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
|`traceOutputOptions`|省略可能な属性です。<br /><br /> トレース リスナーの <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> プロパティ値を指定します。|  
|[カスタム属性]|省略可能な属性です。<br /><br /> リスナーの <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> メソッドによって識別される、リスナー固有の属性の値を指定します。 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> は、<xref:System.Diagnostics.DelimitedListTraceListener> クラスに固有の追加属性の例です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
## <a name="remarks"></a>解説  

 .NET Framework に付属しているリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスから派生したものです。  
  
 トレース リスナーの `name` 属性を指定しなかった場合、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> プロパティは既定で空の文字列 ("") になります。 アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加でき、名前に空の文字列を指定することでリスナーを削除できます。 ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーに一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> コレクション内の個々のトレース リスナーを識別し、管理できるようになります。  
  
> [!NOTE]
> 同じ種類の複数のトレース リスナーを同じ名前で追加すると、その種類と名前のトレース リスナーは 1 つだけになり、`Listeners` コレクションに追加されます。 ただし、複数の同じリスナーをプログラムによって `Listeners` コレクションに追加することはできます。  
  
 `initializeData` 属性の値は、作成するリスナーの種類によって異なります。 すべてのトレース リスナーで `initializeData` を指定する必要はありません。  
  
> [!NOTE]
> `initializeData` 属性を使用すると、"'initializeData' 属性が宣言されていません" というコンパイラ警告が表示されることがあります。 この警告が表示されるのは、`initializeData` 属性を認識しない抽象基本クラス <xref:System.Diagnostics.TraceListener> に対して構成設定が検証されるためです。 通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。  
  
 次の表で、.NET Framework に含まれているトレース リスナーを示し、それらの `initializeData` 属性の値について説明します。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。  トレースおよびデバッグ出力を標準エラー ストリームに書き込むには、`initializeData` 属性を "`true`" に設定します。標準出力ストリームに書き込むには、"`false`" に設定します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> による書き込み先のファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> による書き込み先のファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> による書き込み先のファイルの名前。|  
  
## <a name="configuration-file"></a>構成ファイル  

 この要素は、マシン構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  

 次の例は、`<add>` 要素を使用して、リスナー `console` および `textListener` を トレース ソース `TraceSourceApp` の `Listeners` コレクションに追加する方法を示しています。 `textListener` リスナーにより、トレース出力がファイル myListener.log に書き込まれます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
