---
description: 詳細については、「CorSymVarFlag 列挙型」を参照してください。
title: CorSymVarFlag 列挙体
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 28f4b4775e20703e5dcaa7daf69affd3548aa3f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800462"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="fbbd2-103">CorSymVarFlag 列挙体</span><span class="sxs-lookup"><span data-stu-id="fbbd2-103">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="fbbd2-104">変数がコンパイラによって生成されたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fbbd2-104">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbd2-105">構文</span><span class="sxs-lookup"><span data-stu-id="fbbd2-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="fbbd2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fbbd2-106">Members</span></span>  
  
|<span data-ttu-id="fbbd2-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="fbbd2-107">Member</span></span>|<span data-ttu-id="fbbd2-108">説明</span><span class="sxs-lookup"><span data-stu-id="fbbd2-108">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="fbbd2-109">指定された変数がコンパイラによって生成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="fbbd2-109">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbbd2-110">要件</span><span class="sxs-lookup"><span data-stu-id="fbbd2-110">Requirements</span></span>  

 <span data-ttu-id="fbbd2-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fbbd2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbd2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbbd2-112">See also</span></span>

- [<span data-ttu-id="fbbd2-113">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="fbbd2-113">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
