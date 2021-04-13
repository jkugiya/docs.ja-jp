---
title: memberInfoCacheCreation MDA
description: .NET の memberInfoCacheCreation マネージド デバッグ アシスタント (MDA) について説明します。これは、MemberInfo キャッシュの作成時にアクティブ化されます。
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: 44d279a949ca0b35c46f805e65eb6f61ffb532f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271162"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA

`memberInfoCacheCreation` マネージド デバッグ アシスタント (MDA) は、<xref:System.Reflection.MemberInfo> キャッシュが作成されるとアクティブになります。 これは、リソースに大きな負荷のかかるリフレクション機能をプログラムが使っていることを明確に示すものです。  
  
## <a name="symptoms"></a>現象  

 プログラムがリソースに負荷のかかるリフレクションを使っているため、プログラムのワーキング セットが増加します。  
  
## <a name="cause"></a>原因  

 <xref:System.Reflection.MemberInfo> オブジェクトが関係するリフレクション操作は、コールド ページに格納されているメタデータを読み取る必要があり、一般にプログラムが何らかの種類の遅延バインディング シナリオを使っていることを示すため、リソースに負荷がかかるものと見なされます。  
  
## <a name="resolution"></a>解決方法  

 この MDA を有効にした後にデバッガーでコードを実行するか、または MDA がアクティブになっているときにデバッガーとアタッチすることにより、プログラム内でリフレクションで使われている場所を特定できます。 デバッガーで実行すると、<xref:System.Reflection.MemberInfo> キャッシュが作成された場所を示すスタック トレースが取得され、その情報からプログラムがリフレクションを使っている場所を判断できます。  
  
 解決策は、コードの目的によって異なります。 この MDA は、プログラムに遅延バインディング シナリオがあることを警告します。 事前バインディング シナリオに置き換えることができるかどうかを判断したり、遅延バインディング シナリオのパフォーマンスを検討したりできます。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  

 この MDA は、作成されるすべての <xref:System.Reflection.MemberInfo> キャッシュに対してアクティブ化されます。 パフォーマンスに与える影響はごくわずかです。  
  
## <a name="output"></a>出力  

 MDA は、<xref:System.Reflection.MemberInfo> キャッシュが作成されたことを示すメッセージを出力します。 プログラムがリフレクションを使っている場所を示すスタック トレースを取得するには、デバッガーを使います。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>例  

 次のサンプル コードは、`memberInfoCacheCreation` MDA をアクティブ化します。  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.MemberInfo>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
