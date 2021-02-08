---
description: '詳細について: ICorDebugHeapValue2:: CreateHandle メソッド'
title: ICorDebugHeapValue2::CreateHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: d93fee71441b9c510d517acb9582b8d1d9ce9e10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803660"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="5b081-103">ICorDebugHeapValue2::CreateHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="5b081-103">ICorDebugHeapValue2::CreateHandle Method</span></span>

<span data-ttu-id="5b081-104">この ICorDebugHeapValue2 オブジェクトによって表されるヒープ値に対して指定された型のハンドルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b081-104">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b081-105">構文</span><span class="sxs-lookup"><span data-stu-id="5b081-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b081-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b081-106">Parameters</span></span>  

 `type`  
 <span data-ttu-id="5b081-107">から作成するハンドルの種類を指定する CorDebugHandleType 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="5b081-107">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="5b081-108">入出力このヒープ値の新しいハンドルを表す、値オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b081-108">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b081-109">解説</span><span class="sxs-lookup"><span data-stu-id="5b081-109">Remarks</span></span>  

 <span data-ttu-id="5b081-110">ハンドルは、ヒープ値に関連付けられているアプリケーションドメインに作成され、アプリケーションドメインがアンロードされると無効になります。</span><span class="sxs-lookup"><span data-stu-id="5b081-110">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="5b081-111">同じヒープ値に対してこの関数を複数回呼び出すと、複数のハンドルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5b081-111">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="5b081-112">ハンドルはガベージコレクターのパフォーマンスに影響を与えるため、デバッガーは、一度にアクティブな比較的少数のハンドル (約 256) に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b081-112">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b081-113">要件</span><span class="sxs-lookup"><span data-stu-id="5b081-113">Requirements</span></span>  

 <span data-ttu-id="5b081-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b081-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b081-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b081-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b081-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b081-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b081-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b081-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
