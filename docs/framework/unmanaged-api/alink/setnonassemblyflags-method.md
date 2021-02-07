---
description: '詳細情報: SetNonAssemblyFlags メソッド'
title: SetNonAssemblyFlags メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: 9cf311ec8f04f97da03be626e20c1c07065eac38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662313"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="e052a-103">SetNonAssemblyFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="e052a-103">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="e052a-104">アセンブリ固有ではないフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="e052a-104">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e052a-105">構文</span><span class="sxs-lookup"><span data-stu-id="e052a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e052a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e052a-106">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="e052a-107">ALink フラグ。</span><span class="sxs-lookup"><span data-stu-id="e052a-107">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e052a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e052a-108">Return Value</span></span>  

 <span data-ttu-id="e052a-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="e052a-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e052a-110">要件</span><span class="sxs-lookup"><span data-stu-id="e052a-110">Requirements</span></span>  

 <span data-ttu-id="e052a-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="e052a-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e052a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e052a-112">See also</span></span>

- [<span data-ttu-id="e052a-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e052a-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e052a-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e052a-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e052a-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e052a-115">ALink API</span></span>](index.md)
