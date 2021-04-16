---
description: '詳細情報: <switches> の <add> 要素'
title: <switches> の <add> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: fc47a8518aca1e4e6390d9d7eba97d5fb7a7664e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639719"
---
# <a name="add-element-for-switches"></a>\<switches> の \<add> 要素

トレース スイッチを設定するレベルを指定します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>構文  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**name**|必須の属性です。<br /><br /> スイッチの名前を指定します。 この属性の値は、スイッチ コンストラクターに渡される *displayName* パラメーターに対応します。|  
|**value**|必須の属性です。<br /><br /> スイッチのレベルを指定します。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`switches`|トレース スイッチと、トレース スイッチを設定するレベルを保持します。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## <a name="remarks"></a>解説  

 トレース スイッチのレベルは、構成ファイルに配置して変更できます。 スイッチが <xref:System.Diagnostics.BooleanSwitch> の場合は、オンまたはオフにすることができます。 スイッチが <xref:System.Diagnostics.TraceSwitch> の場合は、別のレベルを割り当てて、アプリケーションが出力するトレース メッセージまたはデバッグ メッセージの種類を指定できます。  
  
## <a name="example"></a>例  

 次の例では、 **\<add>** 要素を使用してトレース スイッチ `General` を <xref:System.Diagnostics.TraceLevel> レベルに設定し、ブール型のトレース スイッチ `Data` を有効にする方法を示します。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [トレースおよびデバッグ設定のスキーマ](index.md)
