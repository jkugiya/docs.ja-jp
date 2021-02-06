---
description: '詳細については、次を参照してください: EnumerateTypeParameters Type:: メソッド'
title: ICorDebugType::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: 5189394cbb39cd133ebce494107f4ca65660bb5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658413"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="c80cc-103">ICorDebugType::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="c80cc-103">ICorDebugType::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="c80cc-104"><xref:System.Type>このテキストの型によって参照されるクラスのパラメーターを格納している、テキスト型へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c80cc-104">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="c80cc-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c80cc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c80cc-106">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="c80cc-107">入出力 `ICorDebugTypeEnum` 型のパラメーターを格納しているのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c80cc-107">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c80cc-108">解説</span><span class="sxs-lookup"><span data-stu-id="c80cc-108">Remarks</span></span>  

 <span data-ttu-id="c80cc-109">を使用することができます、 `EnumerateTypeParameters` [corelementtype:: GetType](icordebugtype-gettype-method.md) によって返される corelementtype 値が ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR、または ELEMENT_TYPE_FNPTR です。</span><span class="sxs-lookup"><span data-stu-id="c80cc-109">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="c80cc-110">パラメーターの数と順序は、型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c80cc-110">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="c80cc-111">ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE: このメソッドが返すに格納されている型パラメーターの数 `ICorDebugTypeEnum` は、対応するクラスの仮引数の型パラメーターの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c80cc-111">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="c80cc-112">たとえば、型がの場合、 `class Dict<String,int32>` はを `EnumerateTypeParameters` `ICorDebugTypeEnum` 表し、シーケンス内でを表すオブジェクトを含むを返し `String` `int32` ます。</span><span class="sxs-lookup"><span data-stu-id="c80cc-112">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="c80cc-113">ELEMENT_TYPE_FNPTR: に格納されている型パラメーターの数 `ICorDebugTypeEnum` が、関数で許容される引数の数を超えています。</span><span class="sxs-lookup"><span data-stu-id="c80cc-113">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="c80cc-114">に格納されている最初の型パラメーターは、関数の戻り値の型であり、 `ICorDebugTypeEnum` 後続の型パラメーターは関数のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="c80cc-114">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="c80cc-115">ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR: 1 つの型パラメーターが返されます。</span><span class="sxs-lookup"><span data-stu-id="c80cc-115">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="c80cc-116">たとえば、型がなどの配列型である場合、 `int32[]` `EnumerateTypeParameters` はを `ICorDebugTypeEnum` 表すオブジェクトを含むを返し `int32` ます。</span><span class="sxs-lookup"><span data-stu-id="c80cc-116">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c80cc-117">要件</span><span class="sxs-lookup"><span data-stu-id="c80cc-117">Requirements</span></span>  

 <span data-ttu-id="c80cc-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c80cc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c80cc-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c80cc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c80cc-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c80cc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c80cc-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c80cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
