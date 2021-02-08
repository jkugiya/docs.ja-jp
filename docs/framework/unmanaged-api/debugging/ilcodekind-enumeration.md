---
description: '詳細情報: ILCodeKind 列挙型'
title: ILCodeKind 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 2d3163b2c601c6f53d9a532fa877c014a67b3e18
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790465"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="c2d82-103">ILCodeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="c2d82-103">ILCodeKind Enumeration</span></span>

<span data-ttu-id="c2d82-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="c2d82-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c2d82-105">デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="c2d82-105">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d82-106">構文</span><span class="sxs-lookup"><span data-stu-id="c2d82-106">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="c2d82-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c2d82-107">Members</span></span>  
  
|<span data-ttu-id="c2d82-108">メンバー名</span><span class="sxs-lookup"><span data-stu-id="c2d82-108">Member name</span></span>|<span data-ttu-id="c2d82-109">説明</span><span class="sxs-lookup"><span data-stu-id="c2d82-109">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="c2d82-110">デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c2d82-110">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="c2d82-111">デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2d82-111">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d82-112">解説</span><span class="sxs-lookup"><span data-stu-id="c2d82-112">Remarks</span></span>  

 <span data-ttu-id="c2d82-113">列挙体のメンバーを `ILCodeKind` [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) メソッドおよび [getlocalvariables ex](icordebugilframe4-getlocalvariableex-method.md) メソッドに渡して、デバッガーがプロファイラー rejit インストルメンテーションに追加された変数にアクセスできるかどうかを判断し、 [getcodeex](icordebugilframe4-getcodeex-method.md) メソッドに渡して、デバッガーがインストルメント化された IL にアクセスできるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c2d82-113">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d82-114">要件</span><span class="sxs-lookup"><span data-stu-id="c2d82-114">Requirements</span></span>  

 <span data-ttu-id="c2d82-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2d82-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d82-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2d82-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2d82-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d82-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d82-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d82-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d82-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2d82-119">See also</span></span>

- [<span data-ttu-id="c2d82-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="c2d82-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c2d82-121">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2d82-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="c2d82-122">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="c2d82-122">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
