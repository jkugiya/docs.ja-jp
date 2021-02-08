---
description: '詳細については、次のページを参照してください: のコードインターフェイス'
title: ICorDebugILCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type:
- apiref
ms.openlocfilehash: 7bf01195f38fd6e046f89e496de3e91e7f8acb33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803634"
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="5fdf0-103">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fdf0-103">ICorDebugILCode Interface</span></span>

<span data-ttu-id="5fdf0-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="5fdf0-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5fdf0-105">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="5fdf0-105">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fdf0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5fdf0-106">Methods</span></span>  
  
|<span data-ttu-id="5fdf0-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5fdf0-107">Method</span></span>|<span data-ttu-id="5fdf0-108">説明</span><span class="sxs-lookup"><span data-stu-id="5fdf0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fdf0-109">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="5fdf0-109">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)|<span data-ttu-id="5fdf0-110">この IL のために定義された例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="5fdf0-110">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fdf0-111">要件</span><span class="sxs-lookup"><span data-stu-id="5fdf0-111">Requirements</span></span>  

 <span data-ttu-id="5fdf0-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fdf0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fdf0-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fdf0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fdf0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fdf0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fdf0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fdf0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdf0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fdf0-116">See also</span></span>

- [<span data-ttu-id="5fdf0-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fdf0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5fdf0-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5fdf0-118">Debugging</span></span>](index.md)
