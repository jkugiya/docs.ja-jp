---
description: 詳細については、「ServiceDebugBehavior」を参照してください。
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 3b384c209524267c72a12d96bc845b694144ba19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715536"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="ebc26-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="ebc26-103">ServiceDebugBehavior</span></span>

<span data-ttu-id="ebc26-104">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="ebc26-104">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc26-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebc26-105">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ebc26-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ebc26-106">Methods</span></span>  

 <span data-ttu-id="ebc26-107">ServiceDebugBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="ebc26-107">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ebc26-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ebc26-108">Properties</span></span>  

 <span data-ttu-id="ebc26-109">ServiceDebugBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ebc26-109">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="ebc26-110">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="ebc26-110">HttpHelpPageEnabled</span></span>  

 <span data-ttu-id="ebc26-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ebc26-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebc26-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebc26-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebc26-113">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="ebc26-113">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="ebc26-114">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="ebc26-114">HttpHelpPageUrl</span></span>  

 <span data-ttu-id="ebc26-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ebc26-115">Data type: string</span></span>  
  
 <span data-ttu-id="ebc26-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebc26-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebc26-117">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="ebc26-117">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="ebc26-118">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="ebc26-118">HttpsHelpPageEnabled</span></span>  

 <span data-ttu-id="ebc26-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ebc26-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebc26-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebc26-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebc26-121">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="ebc26-121">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="ebc26-122">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="ebc26-122">HttpsHelpPageUrl</span></span>  

 <span data-ttu-id="ebc26-123">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ebc26-123">Data type: string</span></span>  
  
 <span data-ttu-id="ebc26-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebc26-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebc26-125">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="ebc26-125">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="ebc26-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="ebc26-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="ebc26-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ebc26-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebc26-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ebc26-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebc26-129">デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージド例外情報を含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebc26-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc26-130">要件</span><span class="sxs-lookup"><span data-stu-id="ebc26-130">Requirements</span></span>  
  
|<span data-ttu-id="ebc26-131">MOF</span><span class="sxs-lookup"><span data-stu-id="ebc26-131">MOF</span></span>|<span data-ttu-id="ebc26-132">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ebc26-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ebc26-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="ebc26-133">Namespace</span></span>|<span data-ttu-id="ebc26-134">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ebc26-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebc26-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebc26-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
