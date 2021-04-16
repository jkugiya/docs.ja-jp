---
description: '詳細情報: <trace> の <listeners> の <add> 要素'
title: <trace> の <listeners> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ffc0823e0c0ce1dcd9d9f19853929496b3248177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639784"
---
# <a name="add-element-for-listeners-for-trace"></a>\<trace> の \<listeners> の \<add> 要素

**Listeners** コレクションにリスナーを追加します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>構文  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**type**|必須の属性です。<br /><br /> リスナーの種類を指定します。 「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定された要件を満たす文字列を使用する必要があります。|  
|**initializeData**|省略可能な属性です。<br /><br /> 指定されたクラスのコンストラクターに渡される文字列。|  
|**name**|省略可能な属性です。<br /><br /> リスナーの名前を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|トレースの `Listeners` コレクションのリスナーにフィルターに追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。 リスナーにより、トレース出力が適切な場所に送られます。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## <a name="remarks"></a>解説  

 <xref:System.Diagnostics.Debug> クラスと <xref:System.Diagnostics.Trace> クラスでは、同じ **Listeners** コレクションが共有されます。 これらのクラスのいずれかのコレクションにリスナー オブジェクトを追加すると、もう一方のクラスでも同じリスナーが使用されます。 リスナー クラスは <xref:System.Diagnostics.TraceListener> から派生します。  
  
 トレース リスナーの `name` 属性を指定しなかった場合、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> は既定で空の文字列 ("") になります。 アプリケーションにリスナーが 1 つしかない場合は、名前を指定せずにリスナーを追加でき、名前に空の文字列を指定することでリスナーを削除できます。 ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーに一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.Debug.Listeners%2A> コレクションと <xref:System.Diagnostics.Trace.Listeners%2A> コレクション内の個々のトレース リスナーを識別し、管理できるようになります。  
  
> [!NOTE]
> 同じ種類の複数のトレース リスナーを同じ名前で追加すると、その種類と名前のトレース リスナーは 1 つだけになり、`Listeners` コレクションに追加されます。 ただし、複数の同じリスナーをプログラムによって `Listeners` コレクションに追加することはできます。  
  
 **initializeData** 属性の値は、作成するリスナーの種類によって異なります。 すべてのトレース リスナーで **initializeData** を指定する必要はありません。  
  
> [!NOTE]
> `initializeData` 属性を使用すると、"'initializeData' 属性が宣言されていません" というコンパイラ警告が表示されることがあります。 この警告が表示されるのは、`initializeData` 属性を認識しない抽象基本クラス <xref:System.Diagnostics.TraceListener> に対して構成設定が検証されるためです。 通常、パラメーターを受け取るコンストラクターを持つトレース リスナーの実装では、この警告を無視できます。  
  
 次の表で、.NET Framework に含まれているトレース リスナーを示し、それらの **initializeData** 属性の値について説明します。  
  
|トレース リスナー クラス|initializeData 属性値|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。  トレースおよびデバッグ出力を <xref:System.Console.Error%2A?displayProperty=nameWithType> に書き込むには、`initializeData` 属性を "`true`" に設定します。<xref:System.Console.Out%2A?displayProperty=nameWithType> に書き込むには、"`false`" に設定します。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.EventSchemaTraceListener> による書き込み先のファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.TextWriterTraceListener> による書き込み先のファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.XmlWriterTraceListener> による書き込み先のファイルの名前。|  
  
## <a name="example"></a>例  

 次の例は、 **\<add>** 要素を使用して、リスナー `MyListener` および `MyEventListener` を **Listeners** コレクションに追加する方法を示しています。 `MyListener` では、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。 `MyEventListener` では、イベント ログにエントリを書き込みます。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
