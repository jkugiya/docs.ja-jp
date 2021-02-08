---
description: '詳細情報: NamedPipeConnectionPoolSettings'
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8d724c7a24f62a8d48797125528eb8a194ece660
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803114"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="030c0-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="030c0-103">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="030c0-104">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="030c0-104">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030c0-105">構文</span><span class="sxs-lookup"><span data-stu-id="030c0-105">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="030c0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="030c0-106">Methods</span></span>  

 <span data-ttu-id="030c0-107">NamedPipeConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="030c0-107">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="030c0-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="030c0-108">Properties</span></span>  

 <span data-ttu-id="030c0-109">NamedPipeConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="030c0-109">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="030c0-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="030c0-110">GroupName</span></span>  

 <span data-ttu-id="030c0-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="030c0-111">Data type: string</span></span>  
  
 <span data-ttu-id="030c0-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030c0-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030c0-113">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="030c0-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="030c0-114">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="030c0-114">IdleTimeout</span></span>  

 <span data-ttu-id="030c0-115">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="030c0-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="030c0-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030c0-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030c0-117">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="030c0-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="030c0-118">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="030c0-118">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="030c0-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="030c0-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="030c0-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="030c0-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="030c0-121">クライアント上の各エンドポイントでの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="030c0-121">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030c0-122">要件</span><span class="sxs-lookup"><span data-stu-id="030c0-122">Requirements</span></span>  
  
|<span data-ttu-id="030c0-123">MOF</span><span class="sxs-lookup"><span data-stu-id="030c0-123">MOF</span></span>|<span data-ttu-id="030c0-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="030c0-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="030c0-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="030c0-125">Namespace</span></span>|<span data-ttu-id="030c0-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="030c0-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="030c0-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="030c0-127">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
