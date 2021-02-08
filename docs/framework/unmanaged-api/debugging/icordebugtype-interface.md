---
description: 詳細については、「のテキストインターフェイス」を参照してください。
title: ICorDebugType インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 4cd668263906ef21e1bb665795425ca3a239c2bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800891"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="7615c-103">ICorDebugType インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7615c-103">ICorDebugType Interface</span></span>

<span data-ttu-id="7615c-104">基本または複合 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="7615c-104">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7615c-105">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="7615c-105">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7615c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-106">Methods</span></span>  
  
|<span data-ttu-id="7615c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-107">Method</span></span>|<span data-ttu-id="7615c-108">説明</span><span class="sxs-lookup"><span data-stu-id="7615c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7615c-109">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-109">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="7615c-110">このによって参照されるクラスのジェネリックパラメーターを参照する、ツールのインターフェイスポインターを取得し <xref:System.Type> `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7615c-110">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7615c-111">GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-111">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="7615c-112">`ICorDebugType`このによって参照されるクラス `ICorDebugType` (存在する場合) の基本クラスを参照するへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7615c-112">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="7615c-113">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-113">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="7615c-114">このの型指定されたコンストラクターを参照する、によるクラスへのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7615c-114">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7615c-115">GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-115">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="7615c-116">`ICorDebugType` <xref:System.Type> このによって参照されるクラスのコンストラクターの最初のジェネリックパラメーターを参照するへのインターフェイスポインターを取得し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7615c-116">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7615c-117">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-117">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="7615c-118">配列型の次元数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7615c-118">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="7615c-119">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-119">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="7615c-120">指定したスタックフレーム内の指定したフィールドトークンによって参照される静的フィールドの値を格納する、ICorDebugValue へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7615c-120">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="7615c-121">GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="7615c-121">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="7615c-122">このによって参照される共通言語ランタイムのネイティブ型を記述する CorElementType 値を取得し <xref:System.Type> `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7615c-122">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7615c-123">解説</span><span class="sxs-lookup"><span data-stu-id="7615c-123">Remarks</span></span>  

 <span data-ttu-id="7615c-124">型がジェネリックの場合、は `ICorDebugClass` インスタンス型を表します。</span><span class="sxs-lookup"><span data-stu-id="7615c-124">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="7615c-125">インターフェイスは、 `ICorDebugType` インスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="7615c-125">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="7615c-126">たとえば、Hashtable はに \<K, V> よって表さ `ICorDebugClass` れますが、hashtable は \<Int32, String> によって表さ `ICorDebugType` れます。</span><span class="sxs-lookup"><span data-stu-id="7615c-126">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7615c-127">非ジェネリック型は、との両方で表され `ICorDebugClass` `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="7615c-127">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="7615c-128">後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="7615c-128">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7615c-129">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7615c-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7615c-130">要件</span><span class="sxs-lookup"><span data-stu-id="7615c-130">Requirements</span></span>  

 <span data-ttu-id="7615c-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7615c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7615c-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7615c-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7615c-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7615c-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7615c-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7615c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7615c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7615c-135">See also</span></span>

- [<span data-ttu-id="7615c-136">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7615c-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
