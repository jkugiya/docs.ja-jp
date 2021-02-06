---
description: '詳細情報: EmitInternalExportedTypes メソッド'
title: EmitInternalExportedTypes メソッド
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
ms.openlocfilehash: 5d23c593988b31c077d3b65b11b73113e164ed74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638302"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="c7179-103">EmitInternalExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="c7179-103">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="c7179-104">アセンブリに追加された型を出力します。</span><span class="sxs-lookup"><span data-stu-id="c7179-104">Emits types added to the assembly.</span></span> <span data-ttu-id="c7179-105">既知の内部型が追加された後に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c7179-105">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7179-106">構文</span><span class="sxs-lookup"><span data-stu-id="c7179-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7179-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7179-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c7179-108">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="c7179-108">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7179-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7179-109">Return Value</span></span>  

 <span data-ttu-id="c7179-110">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="c7179-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7179-111">要件</span><span class="sxs-lookup"><span data-stu-id="c7179-111">Requirements</span></span>  

 <span data-ttu-id="c7179-112">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="c7179-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7179-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7179-113">See also</span></span>

- [<span data-ttu-id="c7179-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7179-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c7179-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7179-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c7179-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c7179-116">ALink API</span></span>](index.md)
