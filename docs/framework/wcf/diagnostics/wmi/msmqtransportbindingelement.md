---
description: 詳細については、「MsmqTransportBindingElement」を参照してください。
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 4b6f363d979972c6ff0a2a378906feeece2ff6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803153"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="02be2-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="02be2-103">MsmqTransportBindingElement</span></span>

<span data-ttu-id="02be2-104">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="02be2-104">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02be2-105">構文</span><span class="sxs-lookup"><span data-stu-id="02be2-105">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="02be2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="02be2-106">Methods</span></span>  

 <span data-ttu-id="02be2-107">MsmqTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="02be2-107">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="02be2-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="02be2-108">Properties</span></span>  

 <span data-ttu-id="02be2-109">MsmqTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="02be2-109">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="02be2-110">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="02be2-110">MaxPoolSize</span></span>  

 <span data-ttu-id="02be2-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02be2-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="02be2-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02be2-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02be2-113">内部 MSMQ メッセージ オブジェクトを含むプールの最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="02be2-113">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="02be2-114">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="02be2-114">QueueTransferProtocol</span></span>  

 <span data-ttu-id="02be2-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="02be2-115">Data type: string</span></span>  
  
 <span data-ttu-id="02be2-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02be2-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02be2-117">このバインディングが使用するキューに置かれた通信チャネルのトランスポートを示す列挙値です。</span><span class="sxs-lookup"><span data-stu-id="02be2-117">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="02be2-118">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="02be2-118">UseActiveDirectory</span></span>  

 <span data-ttu-id="02be2-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="02be2-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="02be2-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02be2-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02be2-121">キューのアドレスを Active Directory を使用して変換する必要があるかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="02be2-121">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02be2-122">要件</span><span class="sxs-lookup"><span data-stu-id="02be2-122">Requirements</span></span>  
  
|<span data-ttu-id="02be2-123">MOF</span><span class="sxs-lookup"><span data-stu-id="02be2-123">MOF</span></span>|<span data-ttu-id="02be2-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="02be2-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="02be2-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="02be2-125">Namespace</span></span>|<span data-ttu-id="02be2-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="02be2-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02be2-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="02be2-127">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
