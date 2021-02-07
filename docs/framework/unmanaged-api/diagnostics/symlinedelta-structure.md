---
description: '詳細情報: SYMLINEDELTA 構造'
title: SYMLINEDELTA 構造体
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: ae00d2be9809b48180d2cd99d05e410624033419
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761448"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="0a3d8-103">SYMLINEDELTA 構造体</span><span class="sxs-lookup"><span data-stu-id="0a3d8-103">SYMLINEDELTA Structure</span></span>

<span data-ttu-id="0a3d8-104">編集の結果として移動されたメソッドについて、シンボルハンドラーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a3d8-104">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3d8-105">構文</span><span class="sxs-lookup"><span data-stu-id="0a3d8-105">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="0a3d8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0a3d8-106">Members</span></span>  
  
|<span data-ttu-id="0a3d8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="0a3d8-107">Member</span></span>|<span data-ttu-id="0a3d8-108">説明</span><span class="sxs-lookup"><span data-stu-id="0a3d8-108">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="0a3d8-109">メソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0a3d8-109">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="0a3d8-110">メソッドが移動された行の数。</span><span class="sxs-lookup"><span data-stu-id="0a3d8-110">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a3d8-111">要件</span><span class="sxs-lookup"><span data-stu-id="0a3d8-111">Requirements</span></span>  

 <span data-ttu-id="0a3d8-112">**ヘッダー:** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="0a3d8-112">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3d8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a3d8-113">See also</span></span>

- [<span data-ttu-id="0a3d8-114">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="0a3d8-114">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
