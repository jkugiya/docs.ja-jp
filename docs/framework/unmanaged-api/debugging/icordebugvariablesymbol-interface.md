---
description: 詳細については、「ICorDebugVariableSymbol インターフェイス」を参照してください。
title: ICorDebugVariableSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: fa3fc1f318627e9175a3066c3bd3eac00929ea60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790543"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="aafbb-103">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aafbb-103">ICorDebugVariableSymbol Interface</span></span>

<span data-ttu-id="aafbb-104">変数のデバッグ シンボル情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-104">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aafbb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-105">Methods</span></span>  
  
|<span data-ttu-id="aafbb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-106">Method</span></span>|<span data-ttu-id="aafbb-107">説明</span><span class="sxs-lookup"><span data-stu-id="aafbb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aafbb-108">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-108">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="aafbb-109">変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-109">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="aafbb-110">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-110">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="aafbb-111">変数のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-111">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="aafbb-112">GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-112">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="aafbb-113">ローカル変数のマネージド スロット インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-113">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="aafbb-114">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-114">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="aafbb-115">変数の値をバイト配列として取得します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-115">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="aafbb-116">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="aafbb-116">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="aafbb-117">バイト配列の値を変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-117">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aafbb-118">解説</span><span class="sxs-lookup"><span data-stu-id="aafbb-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aafbb-119">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="aafbb-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="aafbb-120">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="aafbb-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aafbb-121">要件</span><span class="sxs-lookup"><span data-stu-id="aafbb-121">Requirements</span></span>  

 <span data-ttu-id="aafbb-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aafbb-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aafbb-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aafbb-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aafbb-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aafbb-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aafbb-125">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aafbb-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafbb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="aafbb-126">See also</span></span>

- [<span data-ttu-id="aafbb-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="aafbb-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="aafbb-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="aafbb-128">Debugging</span></span>](index.md)
