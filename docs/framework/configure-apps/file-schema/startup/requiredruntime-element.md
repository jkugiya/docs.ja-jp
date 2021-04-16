---
description: '詳細情報: <requiredRuntime> 要素'
title: <requiredRuntime> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: e9d0a88a65f72ec03f3b2b124920d8265b8bf0c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639849"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime> 要素

バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 この要素は非推奨です。今後は使用しないでください。 代わりに、[`supportedRuntime`](supportedruntime-element.md) 要素を使用してください。

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a>構文

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`version`|省略可能な属性です。<br /><br /> このアプリケーションがサポートする .NET Framework のバージョンを指定する文字列値。 この文字列値は、.NET Framework のインストール ルートの下にあるディレクトリ名と一致する必要があります。 文字列値の内容は解析されません。|
|`safemode`|省略可能な属性です。<br /><br /> ランタイムのスタートアップ コードでレジストリを検索してランタイム バージョンを確認するかどうかを指定します。|

## <a name="safemode-attribute"></a>safemode 属性

|[値]|説明|
|-----------|-----------------|
|`false`|ランタイム スタートアップ コードで、レジストリを検索します。 これが既定値です。|
|`true`|ランタイム スタート アップコードで、レジストリを検索しません。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`startup`|`<requiredRuntime>` 要素が格納されます。|

## <a name="remarks"></a>解説

 ランタイムのバージョン 1.0 のみをサポートするアプリケーションでは、`<requiredRuntime>` 要素を使用する必要があります。 ランタイムのバージョン 1.1 以降を使用しているアプリケーションでは、`<supportedRuntime>` 要素を使用する必要があります。

> [!NOTE]
> [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 関数を使用して構成ファイルを指定する場合は、すべてのバージョンのランタイムに `<requiredRuntime>` 要素を使用する必要があります。 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) を使用すると、`<supportedRuntime>` 要素は無視されます。

 `version` 属性の文字列は、指定されたバージョンの .NET Framework のインストール フォルダー名と一致している必要があります。 この文字列は解釈されません。 ランタイム スタートアップ コードで一致するフォルダーが見つからなかった場合、ランタイムは読み込まれません。スタートアップ コードによってエラー メッセージが表示され、操作が終了します。

> [!NOTE]
> Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードでは、`<requiredRuntime>` 要素は無視されます。

## <a name="example"></a>例

ランタイムのバージョンを構成ファイルで指定する例を次に示します。

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>関連項目

- [スタートアップ設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
