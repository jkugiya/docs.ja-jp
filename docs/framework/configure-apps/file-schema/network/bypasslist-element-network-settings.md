---
title: <bypasslist> 要素 (ネットワーク設定)
description: <bypasslist> ネットワーク設定要素は、.NET Framework 内のプロキシを使用しないアドレスを記述する一連の正規表現を提供します。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 0a03b391c839b7255fdd423a305d474d0e48ad39
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259357"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> 要素 (ネットワーク設定)

プロキシを使用しないアドレスを記述する一連の正規表現を提供します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a>構文  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし。  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[add](add-element-for-bypasslist-network-settings.md)|プロキシ バイパス リストに IP アドレスまたは DNS 名を追加します。|  
|[オフ](clear-element-for-bypasslist-network-settings.md)|バイパス リストをクリアします。|  
|[remove](remove-element-for-bypasslist-network-settings.md)|プロキシ バイパス リストから IP アドレスまたは DNS 名を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="remarks"></a>解説  

 バイパス リストには、<xref:System.Net.WebRequest> インスタンスがプロキシ サーバーを経由せずに直接アクセスする URI を記述する正規表現が含まれます。  
  
 この要素に対して正規表現を指定するときには、注意が必要です。 正規表現 `[a-z]+\\.contoso\\.com` は contoso.com ドメイン内の任意のホストと一致しますが、contoso.com.cpandl.com ドメイン内の任意のホストとも一致します。 contoso.com ドメイン内のホストにのみ一致させるには、アンカー (`$`): `[a-z]+\\.contoso\\.com$` を使用します。
  
 正規表現の詳細については、「[.NET Framework の正規表現](../../../../standard/base-types/regular-expressions.md)」を参照してください。  
  
## <a name="configuration-files"></a>構成ファイル  

 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  

 次の例では、バイパス リストに 2 つのアドレスを追加します。 1 つめは、contoso.com ドメイン内のすべてのサーバーのプロキシをバイパスします。2 つめは、IP アドレスが 192.168 で始まるすべてのアドレスのプロキシをバイパスします。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
