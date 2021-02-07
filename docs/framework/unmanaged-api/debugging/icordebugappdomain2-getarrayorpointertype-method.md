---
description: '詳細について: ICorDebugAppDomain2:: Getarrayorポインター Type メソッド'
title: ICorDebugAppDomain2::GetArrayOrPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754226"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="3de90-103">ICorDebugAppDomain2::GetArrayOrPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="3de90-103">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>

<span data-ttu-id="3de90-104">指定した型、または指定した型へのポインターまたは参照の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="3de90-104">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de90-105">構文</span><span class="sxs-lookup"><span data-stu-id="3de90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3de90-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3de90-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="3de90-107">から作成する基になるネイティブ型 (配列、ポインター、または参照) を指定する CorElementType 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="3de90-107">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="3de90-108">から配列のランク (次元の数)。</span><span class="sxs-lookup"><span data-stu-id="3de90-108">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="3de90-109">が `elementType` ポインターまたは参照型を指定する場合、この値は0である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de90-109">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="3de90-110">から作成される配列、ポインター、または参照の型を表す、の型のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3de90-110">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="3de90-111">入出力構築された `ICorDebugType` 配列、ポインター型、または参照型を表すオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3de90-111">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de90-112">解説</span><span class="sxs-lookup"><span data-stu-id="3de90-112">Remarks</span></span>  

 <span data-ttu-id="3de90-113">*ElementType* の値には、次のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de90-113">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="3de90-114">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="3de90-114">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="3de90-115">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="3de90-115">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="3de90-116">ELEMENT_TYPE_ARRAY または ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="3de90-116">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="3de90-117">*ElementType* の値が ELEMENT_TYPE_PTR または ELEMENT_TYPE_BYREF の場合、 *n ランク* は0にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de90-117">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de90-118">要件</span><span class="sxs-lookup"><span data-stu-id="3de90-118">Requirements</span></span>  

 <span data-ttu-id="3de90-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3de90-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de90-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3de90-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3de90-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3de90-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de90-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de90-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
