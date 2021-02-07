---
description: '詳細情報: TcpTransportBindingElement'
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: b52bb2eb4b40648808459f76e068a6f72f9476a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715146"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="4153a-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4153a-103">TcpTransportBindingElement</span></span>

<span data-ttu-id="4153a-104">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4153a-104">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4153a-105">構文</span><span class="sxs-lookup"><span data-stu-id="4153a-105">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4153a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4153a-106">Methods</span></span>  

 <span data-ttu-id="4153a-107">TcpTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="4153a-107">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4153a-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4153a-108">Properties</span></span>  

 <span data-ttu-id="4153a-109">TcpTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4153a-109">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="4153a-110">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4153a-110">ConnectionPoolSettings</span></span>  

 <span data-ttu-id="4153a-111">データ型 : TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4153a-111">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="4153a-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4153a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4153a-113">接続プールの設定。</span><span class="sxs-lookup"><span data-stu-id="4153a-113">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="4153a-114">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="4153a-114">ListenBacklog</span></span>  

 <span data-ttu-id="4153a-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="4153a-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="4153a-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4153a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4153a-117">保留可能なキュー内の接続要求の最大数です。</span><span class="sxs-lookup"><span data-stu-id="4153a-117">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="4153a-118">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="4153a-118">PortSharingEnabled</span></span>  

 <span data-ttu-id="4153a-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="4153a-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="4153a-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4153a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4153a-121">TCP ポート共有をこの接続で有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="4153a-121">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="4153a-122">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="4153a-122">TeredoEnabled</span></span>  

 <span data-ttu-id="4153a-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="4153a-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="4153a-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4153a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4153a-125">Teredo (ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ) を有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="4153a-125">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4153a-126">要件</span><span class="sxs-lookup"><span data-stu-id="4153a-126">Requirements</span></span>  
  
|<span data-ttu-id="4153a-127">MOF</span><span class="sxs-lookup"><span data-stu-id="4153a-127">MOF</span></span>|<span data-ttu-id="4153a-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="4153a-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4153a-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="4153a-129">Namespace</span></span>|<span data-ttu-id="4153a-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="4153a-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4153a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="4153a-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
