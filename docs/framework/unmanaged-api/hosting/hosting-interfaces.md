---
description: 詳細については、「ホストインターフェイス」を参照してください。
title: ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: 596de1e74fc9c80e5f8b63f40c91a9ef29abcc6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785186"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="a55a9-103">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a55a9-103">Hosting Interfaces</span></span>

<span data-ttu-id="a55a9-104">ここでは、アンマネージホストが共通言語ランタイム (CLR) をアプリケーションに統合するために使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a55a9-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="a55a9-105">.NET Framework バージョン2.0 のホストインターフェイスは、.NET Framework バージョン1.0 および1.1 インターフェイスより優先されます。</span><span class="sxs-lookup"><span data-stu-id="a55a9-105">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="a55a9-106">2つのインターフェイスセットには大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="a55a9-106">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="a55a9-107">これらを混在させると、予期しない動作が発生する可能性があるため、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="a55a9-107">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="a55a9-108">.NET Framework バージョン3.0 および3.5 では、.NET Framework バージョン2.0 のホストインターフェイスが使用され、ホスト機能は導入されません。</span><span class="sxs-lookup"><span data-stu-id="a55a9-108">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="a55a9-109">.NET Framework 4 のホストインターフェイスは、.NET Framework 2.0 インターフェイスより優先されます。</span><span class="sxs-lookup"><span data-stu-id="a55a9-109">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a55a9-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a55a9-110">In This Section</span></span>  

 [<span data-ttu-id="a55a9-111">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="a55a9-111">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a55a9-112">.NET Framework バージョン1.0 および1.1 で導入されたホスティングインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a55a9-112">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a55a9-113">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a55a9-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="a55a9-114">.NET Framework バージョン2.0 で導入されたホスティングインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a55a9-114">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="a55a9-115">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a55a9-115">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="a55a9-116">.NET Framework 4 で導入されたホスティングインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a55a9-116">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a55a9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a55a9-117">Related Sections</span></span>  

 [<span data-ttu-id="a55a9-118">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="a55a9-118">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="a55a9-119">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="a55a9-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="a55a9-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="a55a9-120">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="a55a9-121">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="a55a9-121">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="a55a9-122">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a55a9-122">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="a55a9-123">[ランタイム ホスト](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a55a9-123">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
