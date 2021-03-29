---
description: '詳細情報: ICorProfilerInfo9 インターフェイス'
title: ICorProfilerInfo9 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 44e3d694b426f87ee4e4bc12181f46322b0d246f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805676"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="a0941-103">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0941-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="a0941-104">複数のネイティブ コード バージョンを持つ関数に関する情報を照会するためのメソッドを提供する、[ICorProfilerInfo8](icorprofilerinfo8-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="a0941-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="a0941-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a0941-105">Methods</span></span>  

| <span data-ttu-id="a0941-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a0941-106">Method</span></span>|<span data-ttu-id="a0941-107">説明</span><span class="sxs-lookup"><span data-stu-id="a0941-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a0941-108">GetNativeCodeStartAddresses メソッド</span><span class="sxs-lookup"><span data-stu-id="a0941-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="a0941-109">functionId と rejitId を指定すると、現在存在するこのコードのすべての just-in-time バージョンのネイティブ コードの開始アドレスが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="a0941-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="a0941-110">GetILToNativeMapping3 メソッド</span><span class="sxs-lookup"><span data-stu-id="a0941-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="a0941-111">ネイティブ コードの開始アドレスを指定すると、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a0941-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="a0941-112">GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="a0941-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="a0941-113">ネイティブ コードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="a0941-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a0941-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="a0941-114">Requirements</span></span>  

<span data-ttu-id="a0941-115">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0941-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="a0941-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0941-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a0941-117">**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0941-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a0941-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0941-118">See also</span></span>

- [<span data-ttu-id="a0941-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0941-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
