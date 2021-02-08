---
description: 詳細については、「ICorDebugType2 インターフェイス」を参照してください。
title: ICorDebugType2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 8691cf294e835bef0f5a0ac694110f73577fb5d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800870"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="e7b2e-103">ICorDebugType2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b2e-103">ICorDebugType2 Interface</span></span>

<span data-ttu-id="e7b2e-104">によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するために、を拡張します。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-104">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7b2e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b2e-105">Methods</span></span>  
  
|<span data-ttu-id="e7b2e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b2e-106">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="e7b2e-107">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b2e-107">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="e7b2e-108">この型の [COR_TYPEID](cor-typeid-structure.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-108">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7b2e-109">解説</span><span class="sxs-lookup"><span data-stu-id="e7b2e-109">Remarks</span></span>  

 <span data-ttu-id="e7b2e-110">このインターフェイスは、テキストの型インターフェイスの論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-110">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7b2e-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7b2e-112">例</span><span class="sxs-lookup"><span data-stu-id="e7b2e-112">Example</span></span>  

 <span data-ttu-id="e7b2e-113">次のコードフラグメントは、 [ICorDebugType2:: GetTypeID](icordebugtype2-gettypeid-method.md) メソッドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-113">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="e7b2e-114">要件</span><span class="sxs-lookup"><span data-stu-id="e7b2e-114">Requirements</span></span>  

 <span data-ttu-id="e7b2e-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7b2e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b2e-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7b2e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7b2e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b2e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b2e-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b2e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7b2e-119">See also</span></span>

- [<span data-ttu-id="e7b2e-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b2e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
