---
description: '詳細について: ICorDebugCode4:: EnumerateVariableHomes メソッド'
title: 'ICorDebugCode4:: EnumerateVariableHomes メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 58f5f9063cd22356efd3a77ece9fb43b6b4c1062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710960"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="56326-103">ICorDebugCode4:: EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="56326-103">ICorDebugCode4::EnumerateVariableHomes Method</span></span>

<span data-ttu-id="56326-104">関数のローカル変数および引数に対する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="56326-104">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56326-105">構文</span><span class="sxs-lookup"><span data-stu-id="56326-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56326-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56326-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="56326-107">関数内のローカル変数および引数の列挙子である、の [型](icordebugvariablehomeenum-interface.md) のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56326-107">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56326-108">解説</span><span class="sxs-lookup"><span data-stu-id="56326-108">Remarks</span></span>  

 <span data-ttu-id="56326-109">"ICorDebugEnum" インターフェイスから派生した標準列挙子で[ある、表示変数](icordebugvariablehomeenum-interface.md)[ホーム](icordebugvariablehome-interface.md)オブジェクトを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="56326-109">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="56326-110">コレクションには、同じスロットまたは引数インデックスに対して、関数内の異なるポイントに異なる [ホーム](icordebugvariablehome-interface.md) オブジェクトが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="56326-110">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56326-111">要件</span><span class="sxs-lookup"><span data-stu-id="56326-111">Requirements</span></span>  

 <span data-ttu-id="56326-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56326-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56326-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56326-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56326-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56326-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56326-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56326-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56326-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="56326-116">See also</span></span>

- [<span data-ttu-id="56326-117">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56326-117">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="56326-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="56326-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
