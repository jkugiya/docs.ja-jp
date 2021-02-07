---
description: '詳細情報: Get解像度のスコープメソッド'
title: GetResolutionScope メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: add8ccb1ef6eb0f4b688dcf80563e9280099120d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718396"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="72e20-103">GetResolutionScope メソッド</span><span class="sxs-lookup"><span data-stu-id="72e20-103">GetResolutionScope Method</span></span>

<span data-ttu-id="72e20-104">指定された型のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="72e20-104">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e20-105">構文</span><span class="sxs-lookup"><span data-stu-id="72e20-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="72e20-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72e20-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="72e20-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="72e20-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="72e20-108">参照が必要なファイル。</span><span class="sxs-lookup"><span data-stu-id="72e20-108">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="72e20-109">型が定義されているファイルのトークン。通常は、 [Importfile メソッド](importfile-method.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="72e20-109">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="72e20-110">アセンブリまたはモジュール参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="72e20-110">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72e20-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="72e20-111">Return Value</span></span>  

 <span data-ttu-id="72e20-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="72e20-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e20-113">要件</span><span class="sxs-lookup"><span data-stu-id="72e20-113">Requirements</span></span>  

 <span data-ttu-id="72e20-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="72e20-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e20-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="72e20-115">See also</span></span>

- [<span data-ttu-id="72e20-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72e20-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="72e20-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72e20-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="72e20-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="72e20-118">ALink API</span></span>](index.md)
