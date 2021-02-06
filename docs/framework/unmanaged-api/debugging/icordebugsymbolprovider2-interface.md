---
description: 詳細については、「ICorDebugSymbolProvider2 インターフェイス」を参照してください。
title: ICorDebugSymbolProvider2 インターフェイス
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: b4eaeb29c15da979a522fb20e33a56030889d0c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659518"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="9933f-103">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933f-103">ICorDebugSymbolProvider2 Interface</span></span>

<span data-ttu-id="9933f-104">追加のデバッグシンボル情報を取得するために、この [プロバイダー](icordebugsymbolprovider-interface.md) インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="9933f-104">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9933f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9933f-105">Methods</span></span>  
  
|<span data-ttu-id="9933f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9933f-106">Method</span></span>|<span data-ttu-id="9933f-107">説明</span><span class="sxs-lookup"><span data-stu-id="9933f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9933f-108">GetFrameProps メソッド</span><span class="sxs-lookup"><span data-stu-id="9933f-108">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="9933f-109">メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="9933f-109">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="9933f-110">GetGenericDictionaryInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9933f-110">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="9933f-111">汎用のディクショナリ マップを取得します。</span><span class="sxs-lookup"><span data-stu-id="9933f-111">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9933f-112">解説</span><span class="sxs-lookup"><span data-stu-id="9933f-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9933f-113">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="9933f-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9933f-114">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="9933f-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9933f-115">要件</span><span class="sxs-lookup"><span data-stu-id="9933f-115">Requirements</span></span>  

 <span data-ttu-id="9933f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9933f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9933f-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9933f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9933f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9933f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9933f-119">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9933f-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9933f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9933f-120">See also</span></span>

- [<span data-ttu-id="9933f-121">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933f-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9933f-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9933f-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9933f-123">Debugging</span></span>](index.md)
