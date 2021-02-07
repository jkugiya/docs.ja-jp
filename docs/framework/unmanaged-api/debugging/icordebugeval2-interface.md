---
description: 詳細については、「ICorDebugEval2 インターフェイス」を参照してください。
title: ICorDebugEval2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: 2c279335bdd30b8dc2698f348d9537443b236a45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693760"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="80e05-103">ICorDebugEval2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80e05-103">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="80e05-104">"" は、"" "のように拡張して、ジェネリック型のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="80e05-104">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80e05-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-105">Methods</span></span>  
  
|<span data-ttu-id="80e05-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-106">Method</span></span>|<span data-ttu-id="80e05-107">説明</span><span class="sxs-lookup"><span data-stu-id="80e05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80e05-108">CallParameterizedFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-108">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="80e05-109">指定された "" の呼び出しを設定します。この関数は、コンストラクターが型パラメーターを受け取る型の内部に入れ子にすることも、型パラメーターを受け取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="80e05-109">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="80e05-110">CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-110">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="80e05-111">初期値が null または0の、指定した型の新しい "ICorDebugValue" へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="80e05-111">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="80e05-112">NewParameterizedArray メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-112">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="80e05-113">指定した要素の型と次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="80e05-113">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="80e05-114">NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-114">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="80e05-115">新しいパラメーター化された型オブジェクトをインスタンス化し、オブジェクトのコンストラクターメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="80e05-115">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="80e05-116">NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="80e05-117">コンストラクターメソッドを呼び出さずに、指定したクラスの新しいパラメーター化された型オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="80e05-117">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="80e05-118">NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-118">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="80e05-119">指定したコンテンツを使用して、指定した長さの新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="80e05-119">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="80e05-120">RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="80e05-120">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="80e05-121">このが現在実行している計算を中止し `ICorDebugEval2` ます。</span><span class="sxs-lookup"><span data-stu-id="80e05-121">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80e05-122">解説</span><span class="sxs-lookup"><span data-stu-id="80e05-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80e05-123">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="80e05-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e05-124">要件</span><span class="sxs-lookup"><span data-stu-id="80e05-124">Requirements</span></span>  

 <span data-ttu-id="80e05-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e05-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e05-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80e05-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80e05-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e05-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e05-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e05-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e05-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="80e05-129">See also</span></span>

- [<span data-ttu-id="80e05-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="80e05-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
