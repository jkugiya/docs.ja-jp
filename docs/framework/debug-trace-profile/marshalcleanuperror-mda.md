---
title: marshalCleanupError MDA
description: 一時的な構造体のクリーンアップ中に予期しないエラーが発生したために呼び出される、marshalCleanupError マネージド デバッグ アシスタント (MDA) について確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: e65136f022caa7b1e18a27f7b97a4ef4c27f42d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271192"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="8c4bf-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="8c4bf-103">marshalCleanupError MDA</span></span>

<span data-ttu-id="8c4bf-104">共通言語ランタイム (CLR) が、ネイティブ コードとマネージド コードの境界間でのデータ型のマーシャリングに使用した一時的な構造体とメモリをクリーンアップしようとしたときにエラーが発生すると、`marshalCleanupError` マネージド デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8c4bf-105">現象</span><span class="sxs-lookup"><span data-stu-id="8c4bf-105">Symptoms</span></span>  

 <span data-ttu-id="8c4bf-106">ネイティブ コードとマネージド コードの遷移を実行する場合、スレッド カルチャなどのランタイム状態が復元されない場合、または<xref:System.Runtime.InteropServices.SafeHandle> をクリーンアップしようしてエラーが発生した場合に、メモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8c4bf-107">原因</span><span class="sxs-lookup"><span data-stu-id="8c4bf-107">Cause</span></span>  

 <span data-ttu-id="8c4bf-108">一時的な構造体のクリーンアップ中に予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8c4bf-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="8c4bf-109">Resolution</span></span>  

 <span data-ttu-id="8c4bf-110">すべての <xref:System.Runtime.InteropServices.SafeHandle> デストラクター、ファイナライザー、カスタム マーシャラーの実装を調べ、エラーがないかどうかをレビューします。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8c4bf-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="8c4bf-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="8c4bf-112">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8c4bf-113">出力</span><span class="sxs-lookup"><span data-stu-id="8c4bf-113">Output</span></span>  

 <span data-ttu-id="8c4bf-114">クリーンアップ中に失敗した操作を報告するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="8c4bf-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8c4bf-115">構成</span><span class="sxs-lookup"><span data-stu-id="8c4bf-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c4bf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c4bf-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8c4bf-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="8c4bf-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8c4bf-118">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="8c4bf-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
