---
description: '詳細について: ISymUnmanagedAsyncMethodPropertiesWriter::D efineCatchHandlerILOffset メソッド'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: fcb2c6efa7ea83252a46a9b08cdfa7b2c14f09d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737793"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="f0675-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="f0675-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>

<span data-ttu-id="f0675-104">非同期メソッドをラップする、コンパイラによって生成される catch ハンドラーの IL オフセットを設定します。</span><span class="sxs-lookup"><span data-stu-id="f0675-104">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="f0675-105">生成された catch の IL オフセットは、ユーザーコードメソッドで発生する可能性があっても、ユーザーコード以外のコードであると仮定して、catch を処理するためにデバッガーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0675-105">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="f0675-106">特に、 **CatchHandlerFound** exception イベントに応答して使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0675-106">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0675-107">構文</span><span class="sxs-lookup"><span data-stu-id="f0675-107">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0675-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0675-108">Parameters</span></span>  
  
|<span data-ttu-id="f0675-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0675-109">Parameter</span></span>|<span data-ttu-id="f0675-110">説明</span><span class="sxs-lookup"><span data-stu-id="f0675-110">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="f0675-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f0675-111">Return Value</span></span>  

 <span data-ttu-id="f0675-112">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0675-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0675-113">要件</span><span class="sxs-lookup"><span data-stu-id="f0675-113">Requirements</span></span>  

 <span data-ttu-id="f0675-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f0675-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0675-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0675-115">See also</span></span>

- [<span data-ttu-id="f0675-116">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0675-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
