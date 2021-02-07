---
description: 詳細については、「ICorProfilerInfo9 インターフェイス」を参照してください。
title: ICorProfilerInfo9 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 954cb16d2b789359693f6a8fa3e0f6e19ad19b3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736909"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="e9399-103">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9399-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="e9399-104">複数のネイティブコードバージョンを持つ関数に関する情報を照会するメソッドを提供する [ICorProfilerInfo8](icorprofilerinfo8-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="e9399-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="e9399-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e9399-105">Methods</span></span>  

| <span data-ttu-id="e9399-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e9399-106">Method</span></span>|<span data-ttu-id="e9399-107">説明</span><span class="sxs-lookup"><span data-stu-id="e9399-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="e9399-108">GetNativeCodeStartAddresses メソッド</span><span class="sxs-lookup"><span data-stu-id="e9399-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="e9399-109">指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e9399-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="e9399-110">GetILToNativeMapping3 メソッド</span><span class="sxs-lookup"><span data-stu-id="e9399-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="e9399-111">ネイティブコードの開始アドレスが指定されている場合、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報を返します。</span><span class="sxs-lookup"><span data-stu-id="e9399-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="e9399-112">GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="e9399-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="e9399-113">ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="e9399-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e9399-114">要件</span><span class="sxs-lookup"><span data-stu-id="e9399-114">Requirements</span></span>  

<span data-ttu-id="e9399-115">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9399-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="e9399-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9399-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="e9399-117">**.Net のバージョン:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9399-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e9399-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9399-118">See also</span></span>

- [<span data-ttu-id="e9399-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9399-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
