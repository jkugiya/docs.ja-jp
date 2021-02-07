---
description: '詳細について: ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs メソッド'
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 76b93cdb8c465935a4aaf36090ee44f2b6253a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754174"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="ab7a2-103">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="ab7a2-103">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>

<span data-ttu-id="ab7a2-104">インターフェイス識別子に基づいて、アプリケーションドメイン内のキャッシュされた Windows ランタイム型の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab7a2-104">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab7a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab7a2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab7a2-106">Parameters</span></span>  

 `cReqTypes`  
 <span data-ttu-id="ab7a2-107">から要求される型の数。</span><span class="sxs-lookup"><span data-stu-id="ab7a2-107">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="ab7a2-108">から取得する Windows ランタイム型のマネージ表現に対応するインターフェイス識別子を格納する配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ab7a2-108">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="ab7a2-109">入出力のインターフェイス識別子に基づいて、取得された Windows ランタイム型のキャッシュされたマネージ表現の列挙を可能にする "、"、"" "" ツール "インターフェイスオブジェクトのアドレスへのポインター `iidsToResolve` 。</span><span class="sxs-lookup"><span data-stu-id="ab7a2-109">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab7a2-110">解説</span><span class="sxs-lookup"><span data-stu-id="ab7a2-110">Remarks</span></span>  

 <span data-ttu-id="ab7a2-111">メソッドが特定のインターフェイス識別子に関する情報の取得に失敗した場合、 `ELEMENT_TYPE_END` データの取得に関する問題が原因で、または不明なインターフェイス識別子について、"の型は、" "の種類" になり `ELEMENT_TYPE_VOID` ます。</span><span class="sxs-lookup"><span data-stu-id="ab7a2-111">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab7a2-112">要件</span><span class="sxs-lookup"><span data-stu-id="ab7a2-112">Requirements</span></span>  

 <span data-ttu-id="ab7a2-113">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="ab7a2-113">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="ab7a2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab7a2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab7a2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab7a2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab7a2-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7a2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab7a2-117">See also</span></span>

- [<span data-ttu-id="ab7a2-118">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab7a2-118">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
