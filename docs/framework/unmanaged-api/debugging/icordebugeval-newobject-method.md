---
description: '詳細については、次を参照してください: いいね:: NewObject メソッド'
title: ICorDebugEval::NewObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693955"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="cde01-103">ICorDebugEval::NewObject メソッド</span><span class="sxs-lookup"><span data-stu-id="cde01-103">ICorDebugEval::NewObject Method</span></span>

<span data-ttu-id="cde01-104">新しいオブジェクトインスタンスを割り当て、指定したコンストラクターメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cde01-104">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="cde01-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="cde01-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="cde01-106">代わりに [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="cde01-106">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cde01-107">構文</span><span class="sxs-lookup"><span data-stu-id="cde01-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cde01-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cde01-108">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="cde01-109">から呼び出されるコンストラクター。</span><span class="sxs-lookup"><span data-stu-id="cde01-109">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="cde01-110">[in] `ppArgs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="cde01-110">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="cde01-111">からICorDebugValue オブジェクトの配列。各オブジェクトは、コンストラクターに渡される引数を表します。</span><span class="sxs-lookup"><span data-stu-id="cde01-111">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cde01-112">要件</span><span class="sxs-lookup"><span data-stu-id="cde01-112">Requirements</span></span>  

 <span data-ttu-id="cde01-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cde01-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cde01-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cde01-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cde01-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cde01-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cde01-116">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="cde01-116">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde01-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cde01-117">See also</span></span>

- [<span data-ttu-id="cde01-118">NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="cde01-118">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
