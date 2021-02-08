---
description: '詳細について: ISymUnmanagedAsyncMethodPropertiesWriter::D efineAsyncStepInfo メソッド'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f95436b10041ae5bfd56ca080a9b8ce70748022c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790244"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="64c69-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="64c69-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="64c69-104">現在のメソッドで非同期 await 操作のグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="64c69-104">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="64c69-105">各 yield オフセットは await の戻り命令に一致し、潜在的な yield を識別します。</span><span class="sxs-lookup"><span data-stu-id="64c69-105">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="64c69-106">各 `breakpointMethod` / `breakpointOffset` ペアは、非同期操作が再開される場所を示します。これは、別の方法で実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64c69-106">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64c69-107">構文</span><span class="sxs-lookup"><span data-stu-id="64c69-107">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64c69-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64c69-108">Parameters</span></span>  
  
|<span data-ttu-id="64c69-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64c69-109">Parameter</span></span>|<span data-ttu-id="64c69-110">説明</span><span class="sxs-lookup"><span data-stu-id="64c69-110">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="64c69-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="64c69-111">Return Value</span></span>  

 <span data-ttu-id="64c69-112">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="64c69-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64c69-113">要件</span><span class="sxs-lookup"><span data-stu-id="64c69-113">Requirements</span></span>  

 <span data-ttu-id="64c69-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="64c69-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c69-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="64c69-115">See also</span></span>

- [<span data-ttu-id="64c69-116">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64c69-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
