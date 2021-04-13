---
title: marshaling MDA
description: マーシャリング マネージド デバッグ アシスタント (MDA) について確認します。これは、CLR によってメソッド パラメーターまたは構造体フィールドのマーシャリング情報が設定された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: afe54a2104e05f8fad57c7cbba4988b013aff761
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271175"
---
# <a name="marshaling-mda"></a>marshaling MDA

`marshaling` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、CLR がメソッドのパラメーターまたは構造体のフィールドに関するマーシャリング情報を設定するとアクティブ化されます。 この MDA は、JIT コンパイルされたアセンブリでは機能しません。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  

 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  

 この MDA は、マネージド コンテキストとアンマネージド コンテキストのパラメーターまたはフィールドの型、およびその型を含む構造体またはメソッドを表示します。  フィールドの出力の例を次に示します。  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>構成  

 この MDA の構成では、関連するフィールドまたはメソッドの名前を基にして、報告されたマーシャリング情報をフィルター処理できます。  `methodFilter`、`fieldFilter`、および `match` の各要素を使用してフィルターを指定する方法を次の例に示します。  `name` 属性をアスタリスク (\*) に設定すると、すべてに一致します。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
