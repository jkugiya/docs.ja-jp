---
description: 詳細については、「ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス」を参照してください。
title: ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 4c8b1bc037485e22160af28b59d751859a157499
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790192"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="c7621-103">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7621-103">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>

<span data-ttu-id="c7621-104">各メソッドシンボルに対してオプションの非同期メソッド情報を定義できます。</span><span class="sxs-lookup"><span data-stu-id="c7621-104">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="c7621-105">開いているメソッドでは常にを使用します。つまり、 [Openmethod メソッド](isymunmanagedwriter-openmethod-method.md) と [closemethod メソッド](isymunmanagedwriter-closemethod-method.md)の呼び出しの間です。</span><span class="sxs-lookup"><span data-stu-id="c7621-105">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7621-106">構文</span><span class="sxs-lookup"><span data-stu-id="c7621-106">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="c7621-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="c7621-107">Methods</span></span>  

 <span data-ttu-id="c7621-108">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c7621-108">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="c7621-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="c7621-109">Method</span></span>|<span data-ttu-id="c7621-110">説明</span><span class="sxs-lookup"><span data-stu-id="c7621-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7621-111">DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="c7621-111">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="c7621-112">現在のメソッドで非同期 await 操作のグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="c7621-112">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="c7621-113">各 yield オフセットは await の戻り命令に一致し、潜在的な yield を識別します。</span><span class="sxs-lookup"><span data-stu-id="c7621-113">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="c7621-114">各 `breakpointMethod` / `breakpointOffset` ペアは、非同期操作が再開される場所を識別します。これは、別のメソッドに存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c7621-114">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="c7621-115">DefineCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="c7621-115">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="c7621-116">非同期メソッドをラップする、コンパイラによって生成される catch ハンドラーの IL オフセットを設定します。</span><span class="sxs-lookup"><span data-stu-id="c7621-116">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="c7621-117">生成された catch の IL オフセットは、ユーザーコードメソッドで発生する可能性があっても、catch を非ユーザーコードとして処理するためにデバッガーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7621-117">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="c7621-118">特に、 **CatchHandlerFound** exception イベントに応答して使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7621-118">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="c7621-119">DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="c7621-119">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="c7621-120">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="c7621-120">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7621-121">要件</span><span class="sxs-lookup"><span data-stu-id="c7621-121">Requirements</span></span>  

 <span data-ttu-id="c7621-122">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c7621-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7621-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7621-123">See also</span></span>

- [<span data-ttu-id="c7621-124">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7621-124">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
