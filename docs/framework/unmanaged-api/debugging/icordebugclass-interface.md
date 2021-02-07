---
description: '詳細については、次を参照してください: のクラスインターフェイス'
title: ICorDebugClass インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5ded26a8b3a98bd273bbfe1bfa9efd1bb70d5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711506"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="02ab5-103">ICorDebugClass インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02ab5-103">ICorDebugClass Interface</span></span>

<span data-ttu-id="02ab5-104">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-104">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="02ab5-105">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-105">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02ab5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="02ab5-106">Methods</span></span>  
  
|<span data-ttu-id="02ab5-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="02ab5-107">Method</span></span>|<span data-ttu-id="02ab5-108">説明</span><span class="sxs-lookup"><span data-stu-id="02ab5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02ab5-109">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="02ab5-109">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="02ab5-110">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-110">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="02ab5-111">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="02ab5-111">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="02ab5-112">指定された静的フィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-112">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="02ab5-113">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="02ab5-113">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="02ab5-114">`TypeDef`このクラスのメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-114">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02ab5-115">解説</span><span class="sxs-lookup"><span data-stu-id="02ab5-115">Remarks</span></span>  

 <span data-ttu-id="02ab5-116">インターフェイスは、 `ICorDebugClass` インスタンスジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-116">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="02ab5-117">は、インスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="02ab5-117">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="02ab5-118">たとえば、は `Hashtable<K, V>` で表されますが、は `ICorDebugClass` `Hashtable<Int32, String>` によって表さ `ICorDebugType` れます。</span><span class="sxs-lookup"><span data-stu-id="02ab5-118">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="02ab5-119">非ジェネリック型は、との両方で表され `ICorDebugClass` `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="02ab5-119">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="02ab5-120">後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="02ab5-120">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02ab5-121">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="02ab5-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02ab5-122">要件</span><span class="sxs-lookup"><span data-stu-id="02ab5-122">Requirements</span></span>  

 <span data-ttu-id="02ab5-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02ab5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ab5-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02ab5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02ab5-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02ab5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02ab5-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ab5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ab5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="02ab5-127">See also</span></span>

- [<span data-ttu-id="02ab5-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="02ab5-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
