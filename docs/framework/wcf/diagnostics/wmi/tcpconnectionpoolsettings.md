---
description: '詳細情報: TcpConnectionPoolSettings'
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 927fcba7f94bcbfa80e06479e79bf20986a661e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715198"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="72270-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="72270-103">TcpConnectionPoolSettings</span></span>

<span data-ttu-id="72270-104">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="72270-104">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72270-105">構文</span><span class="sxs-lookup"><span data-stu-id="72270-105">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="72270-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="72270-106">Methods</span></span>  

 <span data-ttu-id="72270-107">TcpConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="72270-107">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="72270-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="72270-108">Properties</span></span>  

 <span data-ttu-id="72270-109">TcpConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="72270-109">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="72270-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="72270-110">GroupName</span></span>  

 <span data-ttu-id="72270-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="72270-111">Data type: string</span></span>  
  
 <span data-ttu-id="72270-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="72270-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72270-113">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="72270-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="72270-114">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="72270-114">IdleTimeout</span></span>  

 <span data-ttu-id="72270-115">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="72270-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="72270-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="72270-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72270-117">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="72270-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="72270-118">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="72270-118">LeaseTimeout</span></span>  

 <span data-ttu-id="72270-119">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="72270-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="72270-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="72270-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72270-121">リース操作を完了する必要がある、タイムアウトまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="72270-121">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="72270-122">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="72270-122">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="72270-123">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="72270-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="72270-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="72270-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72270-125">各エンドポイントの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="72270-125">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72270-126">要件</span><span class="sxs-lookup"><span data-stu-id="72270-126">Requirements</span></span>  
  
|<span data-ttu-id="72270-127">MOF</span><span class="sxs-lookup"><span data-stu-id="72270-127">MOF</span></span>|<span data-ttu-id="72270-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="72270-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="72270-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="72270-129">Namespace</span></span>|<span data-ttu-id="72270-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="72270-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72270-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="72270-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
