---
title: pInvokeLog MDA
description: pInvokeLog マネージド デバッグ アシスタント (MDA) について説明します。これは、.NET 内で実行中に使用される一意のプラットフォーム呼び出しシグネチャごとにアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271461"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA

`pInvokeLog` マネージド デバッグ アシスタント (MDA) は、実行中に使用される一意のプラットフォーム呼び出しシグネチャごとにアクティブになります。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  

 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  

 実行中に使用されるプラットフォーム呼び出しシグネチャを示すメッセージ。  
  
## <a name="configuration"></a>構成  

 各 match 要素で、プラットフォーム呼び出しが行われる .dll ファイルがフィルター処理されます。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [アンマネージ DLL 関数の処理](../interop/consuming-unmanaged-dll-functions.md)
