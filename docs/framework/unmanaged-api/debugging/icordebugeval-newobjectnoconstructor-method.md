---
description: 詳細については、次のページを参照してください:、:、NewObjectNoConstructor メソッド
title: ICorDebugEval::NewObjectNoConstructor メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 4bc8f95da1a554091052dc7e7f49aef4f494578d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693812"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="71688-103">ICorDebugEval::NewObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="71688-103">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="71688-104">コンストラクターメソッドを呼び出さずに、指定した型の新しいオブジェクトインスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="71688-104">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="71688-105">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="71688-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="71688-106">代わりに [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="71688-106">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71688-107">構文</span><span class="sxs-lookup"><span data-stu-id="71688-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71688-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71688-108">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="71688-109">からインスタンス化するオブジェクトの型を表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71688-109">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71688-110">要件</span><span class="sxs-lookup"><span data-stu-id="71688-110">Requirements</span></span>  

 <span data-ttu-id="71688-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71688-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71688-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71688-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71688-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71688-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71688-114">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="71688-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71688-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="71688-115">See also</span></span>

- [<span data-ttu-id="71688-116">NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="71688-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
