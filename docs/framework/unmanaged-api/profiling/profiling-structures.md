---
description: '詳細情報: 構造のプロファイリング'
title: 構造体のプロファイリング
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 7a76c49aaa301ba45c41fb2eb3f7770539dcc6c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798889"
---
# <a name="profiling-structures"></a><span data-ttu-id="eb705-103">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="eb705-103">Profiling Structures</span></span>

<span data-ttu-id="eb705-104">このセクションではプロファイル API で使用されるアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb705-104">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb705-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eb705-105">In This Section</span></span>  

 [<span data-ttu-id="eb705-106">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="eb705-107">共通言語ランタイムに、アセンブリ参照クロージャー ウォークを実行するときに考慮するべき参照アセンブリに関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="eb705-107">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="eb705-108">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-108">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="eb705-109">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="eb705-109">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="eb705-110">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-110">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="eb705-111">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="eb705-111">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="eb705-112">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-112">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="eb705-113">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="eb705-113">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="eb705-114">COR_PRF_FUNCTION_ARGUMENT_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-114">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="eb705-115">関数の引数を左から右方向で表します。</span><span class="sxs-lookup"><span data-stu-id="eb705-115">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="eb705-116">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="eb705-117">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="eb705-117">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="eb705-118">COR_PRF_GC_GENERATION_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="eb705-118">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="eb705-119">ガーベッジ コレクションを実行中のメモリ範囲 (ブロック) を説明します。</span><span class="sxs-lookup"><span data-stu-id="eb705-119">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eb705-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb705-120">Related Sections</span></span>  

 <span data-ttu-id="eb705-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="eb705-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="eb705-122">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="eb705-122">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="eb705-123">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="eb705-123">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="eb705-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb705-124">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="eb705-125">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="eb705-125">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="eb705-126">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="eb705-126">Profiling Enumerations</span></span>](profiling-enumerations.md)
