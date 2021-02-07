---
description: '詳細情報: Okeval:: CreateValue メソッド'
title: ICorDebugEval::CreateValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: f5ea753b5b95c68136e7b799aad88eee5845ea82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694163"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="9ca5f-103">ICorDebugEval::CreateValue メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca5f-103">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="9ca5f-104">初期値を0または null にして、指定した型の値を作成します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-104">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="9ca5f-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9ca5f-106">代わりに [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-106">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca5f-107">構文</span><span class="sxs-lookup"><span data-stu-id="9ca5f-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca5f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ca5f-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="9ca5f-109">から値の型を指定する [Corelementtype](../metadata/corelementtype-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-109">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="9ca5f-110">から型がプリミティブ型ではない場合に、値のクラスを指定 [する、のオブジェクトへ](icordebugclass-interface.md) のポインター。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-110">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9ca5f-111">入出力値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-111">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ca5f-112">解説</span><span class="sxs-lookup"><span data-stu-id="9ca5f-112">Remarks</span></span>  

 <span data-ttu-id="9ca5f-113">`CreateValue` 関数の `ICorDebugValue` 評価で使用するための唯一の目的で、指定された型のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-113">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="9ca5f-114">この値オブジェクトを使用して、ユーザー定数をパラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-114">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="9ca5f-115">値の型がプリミティブ型の場合、初期値は0または null になります。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-115">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="9ca5f-116">の型の値を設定するには、を [使用します](icordebuggenericvalue-setvalue-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-116">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="9ca5f-117">の値 `elementType` が ELEMENT_TYPE_CLASS 場合は、null オブジェクト参照を表す "の値 (で返される) を取得し `ppValue` ます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-117">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="9ca5f-118">このオブジェクトを使用すると、オブジェクト参照パラメーターを持つ関数の評価に null を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-118">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="9ca5f-119">を任意の値に設定することはできません。常に null のままにし `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-119">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca5f-120">要件</span><span class="sxs-lookup"><span data-stu-id="9ca5f-120">Requirements</span></span>  

 <span data-ttu-id="9ca5f-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca5f-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ca5f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca5f-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ca5f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca5f-124">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="9ca5f-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca5f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ca5f-125">See also</span></span>

- [<span data-ttu-id="9ca5f-126">CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca5f-126">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="9ca5f-127">ICorDebugEval インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca5f-127">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
