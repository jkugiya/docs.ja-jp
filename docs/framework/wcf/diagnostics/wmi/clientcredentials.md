---
description: '詳細情報: ClientCredentials'
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 7b0b5a05e5b61de717567de664079f2ed1e20f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757664"
---
# <a name="clientcredentials"></a><span data-ttu-id="098e1-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="098e1-103">ClientCredentials</span></span>

<span data-ttu-id="098e1-104">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="098e1-104">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="098e1-105">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="098e1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="098e1-106">Methods</span></span>  

 <span data-ttu-id="098e1-107">ClientCredentials クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="098e1-107">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="098e1-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="098e1-108">Properties</span></span>  

 <span data-ttu-id="098e1-109">ClientCredentials クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="098e1-109">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="098e1-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="098e1-110">ClientCertificate</span></span>  

 <span data-ttu-id="098e1-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-111">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-113">クライアントがサービスに対して自身を認証するために使用する X.509 証明書です。</span><span class="sxs-lookup"><span data-stu-id="098e1-113">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="098e1-114">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="098e1-114">HttpDigest</span></span>  

 <span data-ttu-id="098e1-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-115">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-117">現在の Http ダイジェスト資格情報です。</span><span class="sxs-lookup"><span data-stu-id="098e1-117">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="098e1-118">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="098e1-118">IssuedToken</span></span>  

 <span data-ttu-id="098e1-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-119">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-121">ローカル セキュリティ トークン サービスにアクセスするために使用されるエンドポイント アドレスおよびバインディングです。</span><span class="sxs-lookup"><span data-stu-id="098e1-121">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="098e1-122">ピア</span><span class="sxs-lookup"><span data-stu-id="098e1-122">Peer</span></span>  

 <span data-ttu-id="098e1-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-123">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-125">ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報です。</span><span class="sxs-lookup"><span data-stu-id="098e1-125">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="098e1-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="098e1-126">ServiceCertificate</span></span>  

 <span data-ttu-id="098e1-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-127">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-129">サービスの X.509 証明書です。</span><span class="sxs-lookup"><span data-stu-id="098e1-129">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="098e1-130">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="098e1-130">SupportInteractive</span></span>  

 <span data-ttu-id="098e1-131">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="098e1-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="098e1-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-133">資格情報が対話的なネゴシエーションをサポートしているかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="098e1-133">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="098e1-134">UserName</span><span class="sxs-lookup"><span data-stu-id="098e1-134">UserName</span></span>  

 <span data-ttu-id="098e1-135">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-135">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-137">クライアントがサービスに対して自身を認証するために使用するユーザー名とパスワードです。</span><span class="sxs-lookup"><span data-stu-id="098e1-137">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="098e1-138">Windows</span><span class="sxs-lookup"><span data-stu-id="098e1-138">Windows</span></span>  

 <span data-ttu-id="098e1-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="098e1-139">Data type: string</span></span>  
  
 <span data-ttu-id="098e1-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="098e1-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="098e1-141">クライアントがサービスに対して自身を認証するために使用する Windows 資格情報です。</span><span class="sxs-lookup"><span data-stu-id="098e1-141">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="098e1-142">要件</span><span class="sxs-lookup"><span data-stu-id="098e1-142">Requirements</span></span>  
  
|<span data-ttu-id="098e1-143">MOF</span><span class="sxs-lookup"><span data-stu-id="098e1-143">MOF</span></span>|<span data-ttu-id="098e1-144">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="098e1-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="098e1-145">名前空間</span><span class="sxs-lookup"><span data-stu-id="098e1-145">Namespace</span></span>|<span data-ttu-id="098e1-146">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="098e1-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="098e1-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="098e1-147">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
