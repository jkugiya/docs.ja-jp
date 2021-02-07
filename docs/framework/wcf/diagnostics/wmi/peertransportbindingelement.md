---
description: 詳細については、「PeerTransportBindingElement」を参照してください。
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: b1ca8020f51a5f9b121f7d238d82b9971d13cdd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757333"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="2fb60-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2fb60-103">PeerTransportBindingElement</span></span>

<span data-ttu-id="2fb60-104">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2fb60-104">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb60-105">構文</span><span class="sxs-lookup"><span data-stu-id="2fb60-105">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2fb60-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2fb60-106">Methods</span></span>  

 <span data-ttu-id="2fb60-107">PeerTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="2fb60-107">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2fb60-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2fb60-108">Properties</span></span>  

 <span data-ttu-id="2fb60-109">PeerTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2fb60-109">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="2fb60-110">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="2fb60-110">ListenIPAddress</span></span>  

 <span data-ttu-id="2fb60-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="2fb60-111">Data type: string</span></span>  
  
 <span data-ttu-id="2fb60-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2fb60-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fb60-113">ピア ノードがメッセージをリッスンする IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="2fb60-113">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="2fb60-114">ポート</span><span class="sxs-lookup"><span data-stu-id="2fb60-114">Port</span></span>  

 <span data-ttu-id="2fb60-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="2fb60-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fb60-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2fb60-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fb60-117">このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。</span><span class="sxs-lookup"><span data-stu-id="2fb60-117">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="2fb60-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2fb60-118">Security</span></span>  

 <span data-ttu-id="2fb60-119">データ型 : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2fb60-119">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="2fb60-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2fb60-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fb60-121">ピア トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="2fb60-121">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb60-122">要件</span><span class="sxs-lookup"><span data-stu-id="2fb60-122">Requirements</span></span>  
  
|<span data-ttu-id="2fb60-123">MOF</span><span class="sxs-lookup"><span data-stu-id="2fb60-123">MOF</span></span>|<span data-ttu-id="2fb60-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="2fb60-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2fb60-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="2fb60-125">Namespace</span></span>|<span data-ttu-id="2fb60-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="2fb60-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fb60-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fb60-127">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
