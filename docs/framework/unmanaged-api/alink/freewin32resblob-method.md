---
description: '詳細情報: FreeWin32ResBlob メソッド'
title: FreeWin32ResBlob メソッド
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
ms.openlocfilehash: 56c83632b623eec76e8e2d24030c79a8262f506f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637944"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="76401-103">FreeWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="76401-103">FreeWin32ResBlob Method</span></span>

<span data-ttu-id="76401-104">Win32 リソース BLOB と、関連付けられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="76401-104">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76401-105">構文</span><span class="sxs-lookup"><span data-stu-id="76401-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="76401-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76401-106">Parameters</span></span>  

 `ppResBlob`  
 <span data-ttu-id="76401-107">解放されるリソース BLOB。</span><span class="sxs-lookup"><span data-stu-id="76401-107">The resource blob to be released.</span></span> <span data-ttu-id="76401-108">このメソッドでは、BLOB ポインターが NULL に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="76401-108">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76401-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="76401-109">Return Value</span></span>  

 <span data-ttu-id="76401-110">メソッドが成功した場合は、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="76401-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76401-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="76401-111">Requirements</span></span>  

 <span data-ttu-id="76401-112">alink.h を必要とします</span><span class="sxs-lookup"><span data-stu-id="76401-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76401-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="76401-113">See also</span></span>

- [<span data-ttu-id="76401-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76401-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="76401-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76401-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="76401-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="76401-116">ALink API</span></span>](index.md)
