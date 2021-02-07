---
description: 詳細については、次の説明を参照してください:、次のメソッド
title: ICorDebugGuidToTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 0ab05cc0689c76c0bb185205ea00c5ccebfcbe03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661000"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="8250a-103">ICorDebugGuidToTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="8250a-103">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="8250a-104">Guid を型情報にマップする、指定された数の [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8250a-104">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8250a-105">構文</span><span class="sxs-lookup"><span data-stu-id="8250a-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8250a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8250a-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8250a-107">から取得する GUID から型へのマッピングオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="8250a-107">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="8250a-108">入出力ポインターの配列。それぞれのポインターが [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトを指します。これは、Windows ランタイム GUID を対応するテキストオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="8250a-108">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8250a-109">入出力実際にで返される [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトの数へのポインター `values` 。</span><span class="sxs-lookup"><span data-stu-id="8250a-109">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8250a-110">解説</span><span class="sxs-lookup"><span data-stu-id="8250a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8250a-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="8250a-111">Requirements</span></span>  

 <span data-ttu-id="8250a-112">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="8250a-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="8250a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8250a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8250a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8250a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8250a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8250a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8250a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8250a-116">See also</span></span>

- [<span data-ttu-id="8250a-117">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8250a-117">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="8250a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8250a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
