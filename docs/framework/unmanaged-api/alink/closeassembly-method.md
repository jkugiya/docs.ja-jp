---
description: '詳細情報: CloseAssembly メソッド'
title: CloseAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 927a66f948f691c00a695c626d9c31950a722cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638393"
---
# <a name="closeassembly-method"></a><span data-ttu-id="27897-103">CloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="27897-103">CloseAssembly Method</span></span>

<span data-ttu-id="27897-104">アセンブリ操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="27897-104">Finalizes assembly operations.</span></span> <span data-ttu-id="27897-105">新しいアセンブリまたは非バインドモジュールを開始する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="27897-105">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27897-106">構文</span><span class="sxs-lookup"><span data-stu-id="27897-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="27897-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27897-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="27897-108">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="27897-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27897-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="27897-109">Return Value</span></span>  

 <span data-ttu-id="27897-110">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="27897-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27897-111">要件</span><span class="sxs-lookup"><span data-stu-id="27897-111">Requirements</span></span>  

 <span data-ttu-id="27897-112">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="27897-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27897-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="27897-113">See also</span></span>

- [<span data-ttu-id="27897-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27897-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="27897-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27897-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="27897-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="27897-116">ALink API</span></span>](index.md)
