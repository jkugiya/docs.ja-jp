---
description: 詳細については、「非推奨の CLR ホストインターフェイスとコクラス」を参照してください。
title: 非推奨の CLR のホスト インターフェイスおよびコクラス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 3d5e8d545dadb4f84c29e2e03a6b23e3729bfe66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785641"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="16d5d-103">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="16d5d-103">Deprecated CLR Hosting Interfaces and Coclasses</span></span>

<span data-ttu-id="16d5d-104">ここでは、アンマネージホストが .NET Framework バージョン1.0 および1.1 の共通言語ランタイム (CLR) をアプリケーションに統合するために使用できるインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="16d5d-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="16d5d-105">これらのインターフェイスは、ホストがランタイムを構成してプロセスに読み込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="16d5d-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16d5d-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="16d5d-106">In This Section</span></span>  

 <span data-ttu-id="16d5d-107">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="16d5d-107">IAppDomainSetup</span></span>  
 <span data-ttu-id="16d5d-108">を構成するためのホストのメソッドを提供 <xref:System.AppDomain> します。</span><span class="sxs-lookup"><span data-stu-id="16d5d-108">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="16d5d-109">ICeeFileGen クラス</span><span class="sxs-lookup"><span data-stu-id="16d5d-109">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="16d5d-110">れネイティブのポータブル実行可能 (PE) ファイルを作成するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="16d5d-110">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="16d5d-111">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16d5d-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="16d5d-112">ホストが CLR 設定を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="16d5d-112">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16d5d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="16d5d-113">Related Sections</span></span>  

 [<span data-ttu-id="16d5d-114">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16d5d-114">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="16d5d-115">.NET Framework バージョン2.0 以降のバージョンで提供されるホストインターフェイスについて説明するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="16d5d-115">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
