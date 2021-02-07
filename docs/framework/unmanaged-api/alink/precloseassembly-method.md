---
description: 詳細については、「PreCloseAssembly メソッド」を参照してください。
title: PreCloseAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: 088a5bba654b3442da64672991d76537e9b4722c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662521"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="87aa3-103">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="87aa3-103">PreCloseAssembly Method</span></span>

<span data-ttu-id="87aa3-104">アセンブリファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="87aa3-104">Closes the assembly file.</span></span> <span data-ttu-id="87aa3-105">他のすべてのファイルを閉じた後、アセンブリファイルを閉じる前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="87aa3-105">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="87aa3-106">バインドされていないモジュールに対しては、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="87aa3-106">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87aa3-107">構文</span><span class="sxs-lookup"><span data-stu-id="87aa3-107">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="87aa3-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87aa3-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="87aa3-109">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="87aa3-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87aa3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="87aa3-110">Return Value</span></span>  

 <span data-ttu-id="87aa3-111">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="87aa3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87aa3-112">要件</span><span class="sxs-lookup"><span data-stu-id="87aa3-112">Requirements</span></span>  

 <span data-ttu-id="87aa3-113">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="87aa3-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87aa3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="87aa3-114">See also</span></span>

- [<span data-ttu-id="87aa3-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87aa3-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="87aa3-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87aa3-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="87aa3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="87aa3-117">ALink API</span></span>](index.md)
