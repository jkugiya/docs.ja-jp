---
title: ID
description: Azure 向けのクラウドネイティブ .NET アプリの設計 |アイデンティティ
ms.date: 01/19/2021
ms.openlocfilehash: b304c8f56996a258fe79e1c38f434a40d773b770
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505662"
---
# <a name="identity"></a><span data-ttu-id="8b546-103">ID</span><span class="sxs-lookup"><span data-stu-id="8b546-103">Identity</span></span>

<span data-ttu-id="8b546-104">ほとんどのソフトウェアアプリケーションは、それらを呼び出すユーザーまたはプロセスに関する知識を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b546-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="8b546-105">アプリケーションと対話するユーザーまたはプロセスはセキュリティプリンシパルと呼ばれ、これらのプリンシパルを認証および承認するプロセスは、id 管理または単に *id* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8b546-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="8b546-106">単純なアプリケーションには、アプリケーション内のすべての id 管理を含めることができますが、この方法は、多くのアプリケーションやさまざまな種類のセキュリティプリンシパルには適していません。</span><span class="sxs-lookup"><span data-stu-id="8b546-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="8b546-107">Windows では、Active Directory を使用して、一元的な認証と承認を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8b546-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="8b546-108">このソリューションは企業ネットワーク内で有効ですが、AD ドメインの外部にあるユーザーまたはアプリケーションが使用できるように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="8b546-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="8b546-109">インターネットベースのアプリケーションとクラウドネイティブアプリの増加により、セキュリティモデルが進化しました。</span><span class="sxs-lookup"><span data-stu-id="8b546-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="8b546-110">現在のクラウドネイティブ id モデルでは、アーキテクチャが分散されると想定されています。</span><span class="sxs-lookup"><span data-stu-id="8b546-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="8b546-111">アプリはどこにでもデプロイでき、どこからでも他のアプリと通信することができます。</span><span class="sxs-lookup"><span data-stu-id="8b546-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="8b546-112">クライアントは、どこからでもこれらのアプリと通信できますが、実際には、クライアントはプラットフォームとデバイスの任意の組み合わせで構成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8b546-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="8b546-113">クラウドネイティブの id ソリューションはオープン標準を使用して、クライアントからの安全なアプリケーションアクセスを実現します。</span><span class="sxs-lookup"><span data-stu-id="8b546-113">Cloud-native identity solutions use open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="8b546-114">これらのクライアントは、Pc や電話の人間のユーザーから、オンラインでホストされている他のアプリまで、世界中の任意のソフトウェアプラットフォームを実行しているトップボックスと IOT デバイスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="8b546-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="8b546-115">最新のクラウドネイティブ id ソリューションでは、通常、セキュリティトークンサービス/サーバー (STS) によって発行されたアクセストークンを、id が決定された後、セキュリティプリンシパルに使用します。</span><span class="sxs-lookup"><span data-stu-id="8b546-115">Modern cloud-native identity solutions typically use access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="8b546-116">アクセストークン (通常は JSON Web トークン (JWT)) には、セキュリティプリンシパルに関する *クレーム* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b546-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="8b546-117">これらの要求には、最小限のユーザー id が含まれますが、アプリケーションがプリンシパルに付与するアクセスレベルを決定するために使用できる他の要求も含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8b546-117">These claims will minimally include the user's identity but may also include other claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="8b546-118">通常、STS はプリンシパルの認証のみを行います。</span><span class="sxs-lookup"><span data-stu-id="8b546-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="8b546-119">リソースへのアクセスレベルを決定することは、アプリケーションの他の部分に残されます。</span><span class="sxs-lookup"><span data-stu-id="8b546-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="8b546-120">リファレンス</span><span class="sxs-lookup"><span data-stu-id="8b546-120">References</span></span>

- [<span data-ttu-id="8b546-121">Microsoft ID プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="8b546-121">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="8b546-122">[前へ](azure-monitor.md)
>[次へ](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="8b546-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
