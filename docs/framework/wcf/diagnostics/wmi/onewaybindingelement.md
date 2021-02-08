---
description: 詳細については、次を参照してください。 One/Bindingelement
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 9c2ccc301bd854c7b85fcc53551ed6def329a8fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803088"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="5d5a3-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="5d5a3-103">OneWayBindingElement</span></span>

<span data-ttu-id="5d5a3-104">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="5d5a3-104">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="5d5a3-105">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5d5a3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d5a3-106">Methods</span></span>  

 <span data-ttu-id="5d5a3-107">OneWayBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-107">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d5a3-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5d5a3-108">Properties</span></span>  

 <span data-ttu-id="5d5a3-109">OneWayBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-109">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="5d5a3-110">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5d5a3-110">ChannelPoolSettings</span></span>  

 <span data-ttu-id="5d5a3-111">データ型 : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="5d5a3-111">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="5d5a3-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5d5a3-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d5a3-113">チャネル プールの設定。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-113">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="5d5a3-114">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="5d5a3-114">MaxAcceptedChannels</span></span>  

 <span data-ttu-id="5d5a3-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="5d5a3-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d5a3-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5d5a3-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d5a3-117">許可されるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-117">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="5d5a3-118">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="5d5a3-118">PacketRoutable</span></span>  

 <span data-ttu-id="5d5a3-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5d5a3-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d5a3-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5d5a3-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d5a3-121">パケットがルーティング可能かどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-121">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d5a3-122">要件</span><span class="sxs-lookup"><span data-stu-id="5d5a3-122">Requirements</span></span>  
  
|<span data-ttu-id="5d5a3-123">MOF</span><span class="sxs-lookup"><span data-stu-id="5d5a3-123">MOF</span></span>|<span data-ttu-id="5d5a3-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="5d5a3-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d5a3-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="5d5a3-125">Namespace</span></span>|<span data-ttu-id="5d5a3-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="5d5a3-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d5a3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d5a3-127">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
