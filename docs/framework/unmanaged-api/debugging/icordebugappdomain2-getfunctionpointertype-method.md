---
description: '詳細情報: ICorDebugAppDomain2:: Getfunctionポインター Type メソッド'
title: ICorDebugAppDomain2::GetFunctionPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: 2b9e10295df40b8e7db82e489fe8a6d28214ff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772394"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="c1f00-103">ICorDebugAppDomain2::GetFunctionPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="c1f00-103">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="c1f00-104">指定されたシグネチャを持つ関数へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c1f00-104">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f00-105">構文</span><span class="sxs-lookup"><span data-stu-id="c1f00-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1f00-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1f00-106">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="c1f00-107">から関数の型引数の数。</span><span class="sxs-lookup"><span data-stu-id="c1f00-107">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="c1f00-108">からポインターの配列。各ポインターは、関数の型引数を表す、テキスト型のオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="c1f00-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="c1f00-109">最初の要素は戻り値の型です。その他の要素はそれぞれパラメーター型です。</span><span class="sxs-lookup"><span data-stu-id="c1f00-109">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="c1f00-110">入出力関数へのポインターを表すオブジェクトのアドレスへのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="c1f00-110">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f00-111">要件</span><span class="sxs-lookup"><span data-stu-id="c1f00-111">Requirements</span></span>  

 <span data-ttu-id="c1f00-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1f00-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f00-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1f00-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1f00-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1f00-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1f00-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f00-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
