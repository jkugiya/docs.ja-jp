---
title: invalidMemberDeclaration MDA
description: invalidMemberDeclaration マネージド デバッグ アシスタントについて確認します。これは、マネージド メソッドを呼び出さずにエラーの HRESULT が COM に返された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: c8d6c69fc6eb4f5f690b02809fdc492da675c3b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272554"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA

`invalidMemberDeclaration` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、COM から呼び出されるメンバーのパラメーターをマーシャリングする方法を判断しているときに、エラーが発生したことを報告するためにアクティブ化されます。  
  
## <a name="symptoms"></a>現象  

 マネージド メソッドが呼び出されることなく、COM にエラーの HRESULT が返されます。  
  
## <a name="cause"></a>原因  

 ほとんどの場合、いずれかのパラメーターに互換性のない <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性があることが原因です。  
  
## <a name="resolution"></a>解決方法  

 パラメーターで有効な <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を指定します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  

 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  

 メンバー名、型名、およびエラー メッセージを含む情報メッセージです。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
