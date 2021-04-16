---
description: '詳細情報: <UseSmallInternalThreadStacks> 要素'
title: <UseSmallInternalThreadStacks> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: eeb253025b32f862926c7315004b1854b8eef928
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639966"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks> 要素

共通言語ランタイム (CLR) で、内部的に使用する特定のスレッドを作成する際、それらのスレッドの既定のスタック サイズを使用するのではなく、明示的なスタック サイズを指定することにより、メモリの使用量を削減するように要求します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> CLR で内部的に使用する特定のスレッドを作成する際に、既定のスタック サイズではなく、明示的なスタック サイズを使用するように要求するかどうかを指定します。 明示的なスタック サイズは、既定のスタック サイズである 1 MB よりも小さくなります。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|true|明示的なスタック サイズを要求します。|  
|false|既定のスタック サイズを使用します。 これは、.NET Framework 4 の既定値です。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  

 この構成要素は、プロセスでの仮想メモリ使用量の削減を要求するために使用されます。要求が受け入れられた場合、CLR で内部スレッド用に使用される明示的なスレッド サイズは、既定のサイズよりも小さくなるためです。  
  
> [!IMPORTANT]
> この構成要素は、絶対的な要件ではなく、CLR に対する要求です。 .NET Framework 4 では、この要求は x86 アーキテクチャについてのみ受け入れられます。 この要素は、将来のバージョンの CLR で完全に無視される可能性もありますし、選択された内部スレッドで常に使用される明示的なスタック サイズに置き換えられる可能性もあります。  
  
 この構成要素を指定すると、CLR で要求が受け入れられた際、仮想メモリの使用量削減と引き換えに、信頼性が低下します。スタック サイズが小さくなると、スタック オーバー フローの発生確率が高まるためです。  
  
## <a name="example"></a>例  

 次の例は、CLR で内部的に使用される特定のスレッドに対して、明示的なスタック サイズを使用するように要求する方法を示しています。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
