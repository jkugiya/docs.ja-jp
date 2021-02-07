---
description: '詳細情報: ServiceCredentials'
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bfd025a8f671a3c5aea537059cde0e751cfa9bb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715549"
---
# <a name="servicecredentials"></a><span data-ttu-id="15ce4-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="15ce4-103">ServiceCredentials</span></span>

<span data-ttu-id="15ce4-104">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="15ce4-104">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ce4-105">構文</span><span class="sxs-lookup"><span data-stu-id="15ce4-105">Syntax</span></span>  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15ce4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="15ce4-106">Methods</span></span>  

 <span data-ttu-id="15ce4-107">ServiceCredentials クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="15ce4-107">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15ce4-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="15ce4-108">Properties</span></span>  

 <span data-ttu-id="15ce4-109">ServiceCredentials クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="15ce4-109">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="15ce4-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="15ce4-110">ClientCertificate</span></span>  

 <span data-ttu-id="15ce4-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-111">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-113">このサービスのための、クライアント証明認証および提供設定です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-113">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="15ce4-114">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="15ce4-114">IssuedTokenAuthentication</span></span>  

 <span data-ttu-id="15ce4-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-115">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-117">このサービスのための、現在発行されているトークンの認証設定です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-117">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="15ce4-118">ピア</span><span class="sxs-lookup"><span data-stu-id="15ce4-118">Peer</span></span>  

 <span data-ttu-id="15ce4-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-119">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-121">ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-121">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="15ce4-122">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="15ce4-122">SecureConversationAuthentication</span></span>  

 <span data-ttu-id="15ce4-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-123">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-125">現在のセキュリティで保護された通信の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ce4-125">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="15ce4-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="15ce4-126">ServiceCertificate</span></span>  

 <span data-ttu-id="15ce4-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-127">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-129">このサービスに関連付けられている証明書です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-129">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="15ce4-130">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="15ce4-130">UserNameAuthentication</span></span>  

 <span data-ttu-id="15ce4-131">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-131">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-133">このサービスのユーザー名/パスワードの設定です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-133">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="15ce4-134">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="15ce4-134">WindowsAuthentication</span></span>  

 <span data-ttu-id="15ce4-135">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="15ce4-135">Data type: string</span></span>  
  
 <span data-ttu-id="15ce4-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15ce4-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15ce4-137">このサービスの Windows 認証の設定です。</span><span class="sxs-lookup"><span data-stu-id="15ce4-137">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ce4-138">要件</span><span class="sxs-lookup"><span data-stu-id="15ce4-138">Requirements</span></span>  
  
|<span data-ttu-id="15ce4-139">MOF</span><span class="sxs-lookup"><span data-stu-id="15ce4-139">MOF</span></span>|<span data-ttu-id="15ce4-140">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="15ce4-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15ce4-141">名前空間</span><span class="sxs-lookup"><span data-stu-id="15ce4-141">Namespace</span></span>|<span data-ttu-id="15ce4-142">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="15ce4-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15ce4-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="15ce4-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
