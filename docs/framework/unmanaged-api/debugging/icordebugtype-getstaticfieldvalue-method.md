---
description: '詳細については、次を参照してください: を参照してください。テキスト:: GetStaticFieldValue メソッド'
title: ICorDebugType::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 378c72f24fedd76f40704ff684781bed124055bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658231"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="3e17b-103">ICorDebugType::GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3e17b-103">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="3e17b-104">指定したスタックフレーム内の指定したフィールドトークンによって参照される静的フィールドの値を格納する、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e17b-104">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e17b-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e17b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e17b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e17b-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="3e17b-107">から `mdFieldDef` 静的フィールドを指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="3e17b-107">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="3e17b-108">からスタックフレームを表す、テキストフレームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e17b-108">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3e17b-109">入出力 `ICorDebugValue` 静的フィールドの値を格納しているのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e17b-109">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e17b-110">解説</span><span class="sxs-lookup"><span data-stu-id="3e17b-110">Remarks</span></span>  

 <span data-ttu-id="3e17b-111">メソッドが使用されるのは、 `GetStaticFieldValue` 型が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE である場合です。この場合、は、"の [型:: GetType](icordebugtype-gettype-method.md) メソッドによって示されます。</span><span class="sxs-lookup"><span data-stu-id="3e17b-111">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="3e17b-112">非ジェネリック型の場合、によって実行される操作は、によって返される、によって `GetStaticFieldValue` 型: [: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) を呼び出すことと同じになります。このクラスは、 [テキスト:: getclass](icordebugtype-getclass-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e17b-112">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="3e17b-113">ジェネリック型の場合、静的フィールド値は特定のインスタンス化に対して相対的になります。</span><span class="sxs-lookup"><span data-stu-id="3e17b-113">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="3e17b-114">また、静的フィールドがスレッド、コンテキスト、またはアプリケーションドメインに対して相対的である可能性がある場合は、デバッガーが適切な値を決定するためにスタックフレームが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3e17b-114">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e17b-115">解説</span><span class="sxs-lookup"><span data-stu-id="3e17b-115">Remarks</span></span>  

 <span data-ttu-id="3e17b-116">`GetStaticFieldValue` は、の呼び出しによって `ICorDebugType::GetType` ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の値が返される場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e17b-116">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e17b-117">要件</span><span class="sxs-lookup"><span data-stu-id="3e17b-117">Requirements</span></span>  

 <span data-ttu-id="3e17b-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e17b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e17b-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e17b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e17b-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e17b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e17b-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e17b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
