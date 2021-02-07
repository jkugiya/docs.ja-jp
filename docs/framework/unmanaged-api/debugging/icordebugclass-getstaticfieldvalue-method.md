---
description: '詳細については、次を参照してください: のクラス:: GetStaticFieldValue メソッド'
title: ICorDebugClass::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: a5406e44491ce89030731c35752066e4943cebfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711522"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="cdef4-103">ICorDebugClass::GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="cdef4-103">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="cdef4-104">指定された静的フィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="cdef4-104">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdef4-105">構文</span><span class="sxs-lookup"><span data-stu-id="cdef4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdef4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cdef4-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="cdef4-107">から `Def` 取得するフィールドを参照するフィールドトークン。</span><span class="sxs-lookup"><span data-stu-id="cdef4-107">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="cdef4-108">からスレッド、コンテキスト、またはアプリケーションドメインの静的を区別するために使用されるフレームを表す、テキストフレームオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdef4-108">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="cdef4-109">静的フィールドがスレッド、コンテキスト、またはアプリケーションドメインに対する相対パスである場合、フレームによって適切な値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="cdef4-109">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="cdef4-110">入出力静的フィールドの値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdef4-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdef4-111">解説</span><span class="sxs-lookup"><span data-stu-id="cdef4-111">Remarks</span></span>  

 <span data-ttu-id="cdef4-112">パラメーター化された型の場合、静的フィールドの値は、特定のインスタンス化に対する相対値になります。</span><span class="sxs-lookup"><span data-stu-id="cdef4-112">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="cdef4-113">したがって、クラスコンストラクターが型のパラメーターを受け取る場合は、では <xref:System.Type> なく、の [型](icordebugtype-getstaticfieldvalue-method.md) を呼び出す必要があり `ICorDebugClass::GetStaticFieldValue` ます。</span><span class="sxs-lookup"><span data-stu-id="cdef4-113">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdef4-114">要件</span><span class="sxs-lookup"><span data-stu-id="cdef4-114">Requirements</span></span>  

 <span data-ttu-id="cdef4-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdef4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdef4-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdef4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdef4-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdef4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdef4-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdef4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
