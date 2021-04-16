---
description: '詳細情報: <startup> 要素'
title: <startup> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 82ece56aaa05376237922b3bd54b6f15967adf8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639823"
---
# <a name="startup-element"></a>\<startup> 要素

共通言語ランタイムのスタートアップ情報を指定します。

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a>構文

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a>属性と要素

 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|省略可能な属性です。<br /><br /> .NET Framework 2.0 のランタイム アクティブ化ポリシーを有効にするか、.NET Framework 4 のアクティブ化ポリシーを使用するかを指定します。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 属性

|[値]|説明|
|-----------|-----------------|
|`true`|選択したランタイムについて、.NET Framework 2.0 のランタイム アクティブ化ポリシーを有効にします。これは、従来のランタイム アクティブ化手法 ([CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)など) を、CLR バージョン 2.0 に制限するのではなく、構成ファイルから選択されたランタイムにバインドするためです。 したがって、CLR バージョン 4 以降が構成ファイルから選択されている場合、以前のバージョンの .NET Framework で作成された混合モードのアセンブリは、選択した CLR バージョンを使って読み込まれます。 この値を設定すると、CLR 1.1 または CLR 2.0 が同じプロセスにロードされなくなり、実質的にインプロセス サイドバイサイド機能が無効になります。|
|`false`|.NET Framework 4 以降の既定のアクティブ化ポリシーを使用します。これは、従来のランタイム アクティブ化手法で、CLR バージョン 1.1 または 2.0 をプロセスに読み込めるようにするためです。 この値を設定すると、混合モードのアセンブリは、.NET Framework 4 以降でビルドされた場合を除き、.NET Framework 4 以降へは読み込まれなくなります。 これが既定値です。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイムのバージョン 1.1 以降でビルドされたアプリケーションは、 **\<supportedRuntime>** 要素を使用します。|
|[\<supportedRuntime>](supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|

## <a name="remarks"></a>解説

 ランタイムのバージョン 1.1 以降を使用して構築されたすべてのアプリケーションでは、 **\<supportedRuntime>** 要素を使用する必要があります。 ランタイムのバージョン 1.0 のみをサポートするアプリケーションでは、 **\<requiredRuntime>** 要素を使用する必要があります。

 Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードでは、 **\<startup>** 要素とその子要素は無視されます。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 属性

 この属性は、アプリケーションで [CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)などのレガシ アクティブ化パスが使用されていて、それらのパスで CLR の以前のバージョンではなくバージョン 4 をアクティブ化したい場合や、アプリケーションは .NET Framework 4 でビルドされているが、以前のバージョンの .NET Framework でビルドされた混合モードのアセンブリに対する依存関係がある場合に便利です。 これらのシナリオでは、この属性を `true` に設定します。

> [!NOTE]
> この属性を `true` に設定すると、CLR 1.1 または CLR 2.0 が同じプロセスにロードされなくなり、実質的にインプロセス サイドバイサイド機能が無効になります (「[COM 相互運用機能の side-by-side 実行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))」を参照してください)。

## <a name="example"></a>例

 ランタイムのバージョンを構成ファイルで指定する例を次に示します。

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>関連項目

- [スタートアップ設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM 相互運用機能の side-by-side 実行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [インプロセスの side-by-side 実行](../../../deployment/in-process-side-by-side-execution.md)
