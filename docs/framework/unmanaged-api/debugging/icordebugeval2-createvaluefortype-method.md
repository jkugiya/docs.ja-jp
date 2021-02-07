---
description: '詳細について: ICorDebugEval2:: CreateValueForType メソッド'
title: ICorDebugEval2::CreateValueForType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 2a8cd129d6194a4870817eb64b79606c395cb055
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693890"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="d22a1-103">ICorDebugEval2::CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="d22a1-103">ICorDebugEval2::CreateValueForType Method</span></span>

<span data-ttu-id="d22a1-104">初期値が0または null の、指定した型の新しい ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d22a1-104">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22a1-105">構文</span><span class="sxs-lookup"><span data-stu-id="d22a1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d22a1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d22a1-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="d22a1-107">から型を表す、の型のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d22a1-107">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d22a1-108">入出力値を表すオブジェクトのアドレスへのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="d22a1-108">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d22a1-109">解説</span><span class="sxs-lookup"><span data-stu-id="d22a1-109">Remarks</span></span>  

 <span data-ttu-id="d22a1-110">`CreateValueForType` 一般化 [Okeval:: CreateValue](icordebugeval-createvalue-method.md) 。などの構築された型を含む任意のオブジェクトの種類を指定でき `List<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="d22a1-110">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="d22a1-111">このメソッドの唯一の目的は、関数の評価に渡すことができる値を生成することです。</span><span class="sxs-lookup"><span data-stu-id="d22a1-111">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="d22a1-112">型はクラスまたは値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d22a1-112">The type must be a class or a value type.</span></span> <span data-ttu-id="d22a1-113">このメソッドを使用して配列値や文字列値を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d22a1-113">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d22a1-114">要件</span><span class="sxs-lookup"><span data-stu-id="d22a1-114">Requirements</span></span>  

 <span data-ttu-id="d22a1-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d22a1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d22a1-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d22a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d22a1-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d22a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d22a1-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d22a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
