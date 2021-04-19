---
title: ID
description: Azure 向けクラウド ネイティブ .NET アプリの設計 | ID
ms.date: 01/19/2021
ms.openlocfilehash: b304c8f56996a258fe79e1c38f434a40d773b770
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505662"
---
# <a name="identity"></a><span data-ttu-id="7c78b-103">ID</span><span class="sxs-lookup"><span data-stu-id="7c78b-103">Identity</span></span>

<span data-ttu-id="7c78b-104">ほとんどのソフトウェア アプリケーションは、呼び出し元のユーザーやプロセスについて何らかの知識を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c78b-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="7c78b-105">アプリケーションと対話するユーザーやプロセスは、セキュリティ プリンシパルと呼ばれます。また、このようなプリンシパルを認証および承認するプロセスは、ID 管理、または単に *ID* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7c78b-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="7c78b-106">単純なアプリケーションでは、ID 管理のすべてをアプリケーション内に含めることができますが、このアプローチは、多くのアプリケーションや多くの種類のセキュリティ プリンシパルではうまく機能しません。</span><span class="sxs-lookup"><span data-stu-id="7c78b-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="7c78b-107">Windows は、Active Directory の使用をサポートして、一元化された認証と承認を提供しています。</span><span class="sxs-lookup"><span data-stu-id="7c78b-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="7c78b-108">このソリューションは、企業ネットワーク内では効果的ですが、AD ドメインの外部にいるユーザーやアプリケーションから使用するようには設計されていません。</span><span class="sxs-lookup"><span data-stu-id="7c78b-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="7c78b-109">インターネットベースのアプリケーションの増加やクラウドネイティブ アプリの台頭に伴い、セキュリティ モデルも進化しています。</span><span class="sxs-lookup"><span data-stu-id="7c78b-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="7c78b-110">現在のクラウドネイティブ ID モデルでは、アーキテクチャは分散されていることが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="7c78b-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="7c78b-111">アプリはどこにでもデプロイされる可能性があり、任意の場所にある他のアプリと通信することがあります。</span><span class="sxs-lookup"><span data-stu-id="7c78b-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="7c78b-112">クライアントはどこからでもこのようなアプリと通信することができます。実際、クライアントは任意の組み合わせのプラットフォームとデバイスから構成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c78b-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="7c78b-113">クライアントからの安全なアプリケーション アクセスを実現するために、クラウドネイティブの ID ソリューションにはオープン スタンダードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="7c78b-113">Cloud-native identity solutions use open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="7c78b-114">このようなクライアントは、PC や電話を使う人間のユーザーから、オンラインのどこかでホストされている他のアプリ、世界のどこかにある任意のソフトウェア プラットフォームを実行しているセットトップ ボックスや IOT デバイスまで、多岐にわたります。</span><span class="sxs-lookup"><span data-stu-id="7c78b-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="7c78b-115">最新のクラウドネイティブ ID ソリューションには、一般的に、セキュリティ プリンシパルの ID が決定されると、セキュアー トークン サービス/サーバー (STS) からセキュリティ プリンシパルに発行されたアクセス トークンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c78b-115">Modern cloud-native identity solutions typically use access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="7c78b-116">アクセス トークンは、通常は JSON Web トークン (JWT) であり、セキュリティ プリンシパルに関する "*クレーム*" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c78b-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="7c78b-117">このようなクレームには、最低でもユーザーの ID が含まれますが、プリンシパルに付与するアクセス レベルを決定するためにアプリケーションに使用できる他のクレームも含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c78b-117">These claims will minimally include the user's identity but may also include other claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="7c78b-118">通常、STS はプリンシパルの認証のみを担当します。</span><span class="sxs-lookup"><span data-stu-id="7c78b-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="7c78b-119">リソースへのアクセス レベルの決定は、アプリケーションの他の部分に委ねられます。</span><span class="sxs-lookup"><span data-stu-id="7c78b-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="7c78b-120">リファレンス</span><span class="sxs-lookup"><span data-stu-id="7c78b-120">References</span></span>

- [<span data-ttu-id="7c78b-121">Microsoft ID プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="7c78b-121">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="7c78b-122">[前へ](azure-monitor.md)
>[次へ](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="7c78b-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
