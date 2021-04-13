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
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="47aaa-103">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="47aaa-103">invalidMemberDeclaration MDA</span></span>

<span data-ttu-id="47aaa-104">`invalidMemberDeclaration` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、COM から呼び出されるメンバーのパラメーターをマーシャリングする方法を判断しているときに、エラーが発生したことを報告するためにアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="47aaa-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="47aaa-105">現象</span><span class="sxs-lookup"><span data-stu-id="47aaa-105">Symptoms</span></span>  

 <span data-ttu-id="47aaa-106">マネージド メソッドが呼び出されることなく、COM にエラーの HRESULT が返されます。</span><span class="sxs-lookup"><span data-stu-id="47aaa-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="47aaa-107">原因</span><span class="sxs-lookup"><span data-stu-id="47aaa-107">Cause</span></span>  

 <span data-ttu-id="47aaa-108">ほとんどの場合、いずれかのパラメーターに互換性のない <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性があることが原因です。</span><span class="sxs-lookup"><span data-stu-id="47aaa-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="47aaa-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="47aaa-109">Resolution</span></span>  

 <span data-ttu-id="47aaa-110">パラメーターで有効な <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="47aaa-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="47aaa-111">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="47aaa-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="47aaa-112">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="47aaa-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="47aaa-113">出力</span><span class="sxs-lookup"><span data-stu-id="47aaa-113">Output</span></span>  

 <span data-ttu-id="47aaa-114">メンバー名、型名、およびエラー メッセージを含む情報メッセージです。</span><span class="sxs-lookup"><span data-stu-id="47aaa-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="47aaa-115">構成</span><span class="sxs-lookup"><span data-stu-id="47aaa-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47aaa-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="47aaa-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="47aaa-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="47aaa-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="47aaa-118">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="47aaa-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
