---
description: '詳細について: ISymUnmanagedWriter3:: OpenMethod2 メソッド'
title: ISymUnmanagedWriter3::OpenMethod2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 7e76be03598599a6498ed45bc3799c6d6f21e088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761695"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="884ab-103">ISymUnmanagedWriter3::OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="884ab-103">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="884ab-104">メソッドを開き、イメージ内の実際のセクションオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="884ab-104">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="884ab-105">構文</span><span class="sxs-lookup"><span data-stu-id="884ab-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="884ab-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="884ab-106">Parameters</span></span>  

 `method`  
 <span data-ttu-id="884ab-107">から開くメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="884ab-107">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="884ab-108">からイメージ内のセクションオフセット。</span><span class="sxs-lookup"><span data-stu-id="884ab-108">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="884ab-109">からイメージ内のオフセット。</span><span class="sxs-lookup"><span data-stu-id="884ab-109">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="884ab-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="884ab-110">Return Value</span></span>  

 <span data-ttu-id="884ab-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="884ab-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="884ab-112">要件</span><span class="sxs-lookup"><span data-stu-id="884ab-112">Requirements</span></span>  

 <span data-ttu-id="884ab-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="884ab-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="884ab-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="884ab-114">See also</span></span>

- [<span data-ttu-id="884ab-115">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="884ab-115">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="884ab-116">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="884ab-116">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
