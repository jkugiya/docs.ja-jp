---
description: '詳細情報: ServiceMetadataBehavior'
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1b1438013ec667b10b300d898687abf6f33f96fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715484"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="2db0e-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="2db0e-103">ServiceMetadataBehavior</span></span>

<span data-ttu-id="2db0e-104">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="2db0e-104">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db0e-105">構文</span><span class="sxs-lookup"><span data-stu-id="2db0e-105">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2db0e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2db0e-106">Methods</span></span>  

 <span data-ttu-id="2db0e-107">ServiceMetadataBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="2db0e-107">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2db0e-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2db0e-108">Properties</span></span>  

 <span data-ttu-id="2db0e-109">ServiceMetadataBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2db0e-109">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="2db0e-110">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="2db0e-110">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="2db0e-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="2db0e-111">Data type: string</span></span>  
  
 <span data-ttu-id="2db0e-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2db0e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db0e-113">サービスがメタデータ要求をリダイレクトする場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="2db0e-113">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="2db0e-114">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="2db0e-114">HttpGetEnabled</span></span>  

 <span data-ttu-id="2db0e-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="2db0e-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="2db0e-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2db0e-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db0e-117">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="2db0e-117">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="2db0e-118">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="2db0e-118">HttpGetUrl</span></span>  

 <span data-ttu-id="2db0e-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="2db0e-119">Data type: string</span></span>  
  
 <span data-ttu-id="2db0e-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2db0e-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db0e-121">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="2db0e-121">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="2db0e-122">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="2db0e-122">HttpsGetEnabled</span></span>  

 <span data-ttu-id="2db0e-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="2db0e-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="2db0e-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2db0e-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db0e-125">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="2db0e-125">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="2db0e-126">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="2db0e-126">HttpsGetUrl</span></span>  

 <span data-ttu-id="2db0e-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="2db0e-127">Data type: string</span></span>  
  
 <span data-ttu-id="2db0e-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2db0e-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2db0e-129">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="2db0e-129">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db0e-130">要件</span><span class="sxs-lookup"><span data-stu-id="2db0e-130">Requirements</span></span>  
  
|<span data-ttu-id="2db0e-131">MOF</span><span class="sxs-lookup"><span data-stu-id="2db0e-131">MOF</span></span>|<span data-ttu-id="2db0e-132">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="2db0e-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2db0e-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="2db0e-133">Namespace</span></span>|<span data-ttu-id="2db0e-134">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="2db0e-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2db0e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="2db0e-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
