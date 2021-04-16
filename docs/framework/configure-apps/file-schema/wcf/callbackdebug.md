---
description: '詳細情報: <callbackDebug>'
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 911d738764baa800831c19f4e5d181118d1d3e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639212"
---
# \<callbackDebug>

<span data-ttu-id="996b7-102">Windows Communication Foundation (WCF) コールバック オブジェクトのサービス デバッグを指定します。</span><span class="sxs-lookup"><span data-stu-id="996b7-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="996b7-103">構文</span><span class="sxs-lookup"><span data-stu-id="996b7-103">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="996b7-104">種類</span><span class="sxs-lookup"><span data-stu-id="996b7-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="996b7-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="996b7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="996b7-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="996b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="996b7-107">属性</span><span class="sxs-lookup"><span data-stu-id="996b7-107">Attributes</span></span>  
  
|<span data-ttu-id="996b7-108">属性</span><span class="sxs-lookup"><span data-stu-id="996b7-108">Attribute</span></span>|<span data-ttu-id="996b7-109">説明</span><span class="sxs-lookup"><span data-stu-id="996b7-109">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="996b7-110">クライアント コールバック オブジェクトが SOAP エラー内のマネージド例外情報をサービスに返すかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="996b7-110">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="996b7-111">プログラムでこの属性を `true` に設定すると、デバッグするために、クライアント コールバック オブジェクト内のマネージド例外情報がサービスに戻るフローを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="996b7-111">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="996b7-112">**注:**  マネージド例外情報をクライアントに返すことは、セキュリティ リスクになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="996b7-112">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="996b7-113">これは、例外の詳細が、認証されていないクライアントによって使用可能な内部サービスの実装に関する情報を公開するためです。</span><span class="sxs-lookup"><span data-stu-id="996b7-113">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="996b7-114">子要素</span><span class="sxs-lookup"><span data-stu-id="996b7-114">Child Elements</span></span>  

 <span data-ttu-id="996b7-115">なし。</span><span class="sxs-lookup"><span data-stu-id="996b7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="996b7-116">親要素</span><span class="sxs-lookup"><span data-stu-id="996b7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="996b7-117">要素</span><span class="sxs-lookup"><span data-stu-id="996b7-117">Element</span></span>|<span data-ttu-id="996b7-118">説明</span><span class="sxs-lookup"><span data-stu-id="996b7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="996b7-119">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="996b7-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="996b7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="996b7-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
