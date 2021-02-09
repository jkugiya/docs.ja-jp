---
description: '詳細情報: Windows ストア アプリのネットワーク分離'
title: Windows ストア アプリのネットワーク分離
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: cc805cb5d5d761bb79b6a307caef6c809aabed16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785720"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="98f05-103">Windows ストア アプリのネットワーク分離</span><span class="sxs-lookup"><span data-stu-id="98f05-103">Network Isolation for Windows Store Apps</span></span>

<span data-ttu-id="98f05-104">名前空間 <xref:System.Net>、<xref:System.Net.Http>、<xref:System.Net.Http.Headers> 内のクラスを使用して、Windows ストア アプリまたはデスクトップ アプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="98f05-104">Classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="98f05-105">Windows ストア アプリで使用する場合、これらの名前空間内のクラスは、Windows 8 で使用されるアプリケーション セキュリティ モデルの一部であるネットワーク分離の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="98f05-105">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by Windows 8.</span></span> <span data-ttu-id="98f05-106">システムでネットワーク アクセスが許可されるように、Windows ストア アプリのアプリ マニフェストで適切なネットワーク機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98f05-106">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="98f05-107">ネットワーク分離のチェックリスト</span><span class="sxs-lookup"><span data-stu-id="98f05-107">Checklist for Network Isolation</span></span>  

<span data-ttu-id="98f05-108">Windows ストア アプリに対してネットワークの分離が適切に構成されているかどうかを、このチェックリストを使って確認してください。</span><span class="sxs-lookup"><span data-stu-id="98f05-108">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1. <span data-ttu-id="98f05-109">アプリが必要とするネットワーク アクセス要求の方向を確認します。</span><span class="sxs-lookup"><span data-stu-id="98f05-109">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="98f05-110">これには、クライアント側から開始される送信要求と、受信側が送信を要求していない受信要求とがあります。両方の種類のネットワーク要求を組み合わせたものもあります。</span><span class="sxs-lookup"><span data-stu-id="98f05-110">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2. <span data-ttu-id="98f05-111">アプリの通信相手となるネットワーク リソースの種類を確認します。</span><span class="sxs-lookup"><span data-stu-id="98f05-111">Determine the type of network resources that the app will communicate with.</span></span> <span data-ttu-id="98f05-112">アプリの通信相手は、ホーム ネットワークまたは職場ネットワーク上の信頼済みリソースである場合があります。</span><span class="sxs-lookup"><span data-stu-id="98f05-112">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="98f05-113">または、インターネット上のリソースと通信することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="98f05-113">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="98f05-114">その両方の種類のネットワーク リソースにアクセスする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="98f05-114">An app might need access to both types of network resources.</span></span>  
  
3. <span data-ttu-id="98f05-115">アプリ マニフェストで、必要最小限のネットワーク分離機能を構成します。</span><span class="sxs-lookup"><span data-stu-id="98f05-115">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4. <span data-ttu-id="98f05-116">アプリを展開して実行し、トラブルシューティングのためのネットワーク分離ツールを使用してテストします。</span><span class="sxs-lookup"><span data-stu-id="98f05-116">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
<span data-ttu-id="98f05-117">ネットワーク機能の構成と、ネットワーク分離のトラブルシューティングに使用する分離ツールの詳細については、Windows 8.x Store 開発者向けドキュメントで、[ネットワーク分離の機能を構成する方法](/previous-versions/windows/apps/hh770532(v=win.10))に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98f05-117">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98f05-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="98f05-118">See also</span></span>

- <span data-ttu-id="98f05-119">[Web サービスへの接続](/previous-versions/windows/apps/hh761504(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="98f05-119">[Connecting to a web service](/previous-versions/windows/apps/hh761504(v=win.10))</span></span>
- <span data-ttu-id="98f05-120">[ネットワーク分離のガイドラインとチェックリスト](/previous-versions/windows/apps/hh770532(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="98f05-120">[Guidelines and checklist for network isolation](/previous-versions/windows/apps/hh770532(v=win.10))</span></span>
- <span data-ttu-id="98f05-121">[クイック スタート: HttpClient を使って接続する](/previous-versions/windows/apps/hh781239(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="98f05-121">[Quickstart: Connecting using HttpClient](/previous-versions/windows/apps/hh781239(v=win.10))</span></span>
- <span data-ttu-id="98f05-122">[HttpClient ハンドラーを使う方法](/previous-versions/windows/apps/hh781241(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="98f05-122">[How to use HttpClient handlers](/previous-versions/windows/apps/hh781241(v=win.10))</span></span>
- <span data-ttu-id="98f05-123">[HttpClient の接続をセキュリティで保護する方法](/previous-versions/windows/apps/hh781240(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="98f05-123">[How to secure HttpClient connections](/previous-versions/windows/apps/hh781240(v=win.10))</span></span>
- [<span data-ttu-id="98f05-124">HttpClient のサンプル</span><span class="sxs-lookup"><span data-stu-id="98f05-124">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
