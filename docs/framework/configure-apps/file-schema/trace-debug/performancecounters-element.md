---
description: '詳細情報: <performanceCounters> 要素'
title: <performanceCounters> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 3a9a6c42575be3fc7fb5c5d80ffecd940894e164
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639576"
---
# <a name="performancecounters-element"></a>\<performanceCounters> 要素

パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a>構文

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|filemappingsize|必須の属性です。<br /><br /> パフォーマンス カウンターが共有するグローバル メモリのサイズをバイト単位で指定します。 既定値は 524288 です。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|

## <a name="remarks"></a>解説

パフォーマンス カウンターでは、パフォーマンス データをパブリッシュするのに、メモリ マップト ファイル (共有メモリ) が使用されます。  一度に使用できるインスタンスの数は、共有メモリのサイズによって決まります。  共有メモリには、グローバル共有メモリと個別の共有メモリの 2 種類があります。  グローバル共有メモリは、.NET Framework バージョン 1.0 または 1.1 と共にインストールされたすべてのパフォーマンス カウンター カテゴリによって使用されます。  .NET Framework バージョン 2.0 と共にインストールされたパフォーマンス カウンター カテゴリでは、個別の共有メモリが使用され、各パフォーマンス カウンター カテゴリごとに独自のメモリが確保されます。

グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。  既定のサイズは 524,288 バイトで、最大サイズは 33,554,432 バイト、最小サイズは 32,768 バイトです。  グローバル共有メモリはすべてのプロセスとカテゴリによって共有されるため、最初の作成者がサイズを指定します。  アプリケーション構成ファイルでサイズを定義する場合、そのサイズは、そのアプリケーションがパフォーマンス カウンターを実行する最初のアプリケーションである場合にのみ使用されます。  そのため、`filemappingsize` 値を指定するための正しい場所は Machine.config ファイルになります。  グローバル共有メモリ内のメモリは個々のパフォーマンス カウンターによって解放することができないため、名前の異なるパフォーマンス カウンター インスタンスが多数作成されると、グローバル共有メモリは最終的に使い果たされます。

個別の共有メモリのサイズについては、レジストリ キー HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\ *\<category name>* \Performance の DWORD FileMappingSize の値が最初に参照され、その次に、構成ファイル内のグローバル共有メモリ用に指定された値が参照されます。 FileMappingSize の値が存在しない場合、個別の共有メモリ サイズは、構成ファイル内のグローバル設定の 4 分の 1 (1/4) に設定されます。

## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
