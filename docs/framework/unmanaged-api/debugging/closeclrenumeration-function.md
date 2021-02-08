---
description: '詳細情報: CloseCLREnumeration 関数'
title: CloseCLREnumeration 関数
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 7669332cc23b78afbb3bf597e7d208a5f707aae5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772771"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="9b8dd-103">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="9b8dd-103">CloseCLREnumeration Function</span></span>

<span data-ttu-id="9b8dd-104">[列挙 Ateclrs 関数](enumerateclrs-function.md)によって返されるハンドルの配列にある有効な共通言語ランタイム (CLR) の継続スタートアップイベントをすべて閉じ、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-104">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8dd-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b8dd-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b8dd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b8dd-106">Parameters</span></span>  

 `pHandleArray`  
 <span data-ttu-id="9b8dd-107">から [列挙機能](enumerateclrs-function.md)から返されたイベントハンドルの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-107">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="9b8dd-108">から [列挙型 Ateclrs 関数](enumerateclrs-function.md)から返された CLR 文字列パスの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-108">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="9b8dd-109">[in] `pHandleArray` または `pStringArray` (これらは同じです) のサイズ (長さ) を含む DWORD。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-109">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b8dd-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b8dd-110">Return Value</span></span>  

 <span data-ttu-id="9b8dd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b8dd-111">S_OK</span></span>  
 <span data-ttu-id="9b8dd-112">[列挙 Ateclrs 関数](enumerateclrs-function.md)によって開かれたハンドルが閉じられ、ハンドルおよび文字列配列に割り当てられたメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-112">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="9b8dd-113">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9b8dd-113">E_INVALIDARG</span></span>  
 <span data-ttu-id="9b8dd-114">`pHandleArray` の長さが、`dwArrayLength` に渡された長さと一致しません。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-114">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="9b8dd-115">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="9b8dd-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9b8dd-116">`pHandleArray` および `pStringArray` のメモリを解放できません。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-116">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b8dd-117">要件</span><span class="sxs-lookup"><span data-stu-id="9b8dd-117">Requirements</span></span>  

 <span data-ttu-id="9b8dd-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b8dd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b8dd-119">**ヘッダー:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="9b8dd-119">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="9b8dd-120">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="9b8dd-120">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="9b8dd-121">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9b8dd-121">**.NET Framework Versions:** 3.5 SP1</span></span>
