---
title: invalidFunctionPointerInDelegate MDA
description: invalidFunctionPointerInDelegate マネージド デバッグ アシスタント (MDA) について確認します。これは、デリゲートを作成するために無効な関数ポインターが渡された場合に呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 8072d35a45cb1e0590aa5533210d0e0f86913164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272619"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA

ネイティブ関数ポインターに対するデリゲートを作成するときに、無効な関数ポインターが渡されると、`invalidFunctionPointerInDelegate` マネージド デバッグ アシスタント (MDA) がアクティブ化されます。  
  
## <a name="symptoms"></a>現象  

 関数ポインターでデリゲートを使用すると、アクセス違反または予期しないメモリの破損が発生します。  
  
## <a name="cause"></a>原因  

 無効な関数ポインターが指定されました。  
  
## <a name="resolution"></a>解決方法  

 有効な関数ポインターを指定します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  

 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  

 無効な関数ポインター。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
