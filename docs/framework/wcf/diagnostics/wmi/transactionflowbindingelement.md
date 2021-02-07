---
description: '詳細情報: TransactionFlowBindingElement'
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 6a96a83c563affdaef01a12d64bc1c13ab2f719e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757138"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="63f34-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="63f34-103">TransactionFlowBindingElement</span></span>

<span data-ttu-id="63f34-104">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="63f34-104">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f34-105">構文</span><span class="sxs-lookup"><span data-stu-id="63f34-105">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="63f34-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="63f34-106">Methods</span></span>  

 <span data-ttu-id="63f34-107">TransactionFlowBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="63f34-107">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="63f34-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="63f34-108">Properties</span></span>  

 <span data-ttu-id="63f34-109">TransactionFlowBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="63f34-109">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="63f34-110">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="63f34-110">IssuedTokens</span></span>  

 <span data-ttu-id="63f34-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="63f34-111">Data type: string</span></span>  
  
 <span data-ttu-id="63f34-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="63f34-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63f34-113">発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="63f34-113">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="63f34-114">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="63f34-114">TransactionProtocol</span></span>  

 <span data-ttu-id="63f34-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="63f34-115">Data type: string</span></span>  
  
 <span data-ttu-id="63f34-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="63f34-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63f34-117">トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="63f34-117">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="63f34-118">トランザクション</span><span class="sxs-lookup"><span data-stu-id="63f34-118">Transactions</span></span>  

 <span data-ttu-id="63f34-119">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="63f34-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="63f34-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="63f34-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63f34-121">受信トランザクションをサポートするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="63f34-121">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f34-122">要件</span><span class="sxs-lookup"><span data-stu-id="63f34-122">Requirements</span></span>  
  
|<span data-ttu-id="63f34-123">MOF</span><span class="sxs-lookup"><span data-stu-id="63f34-123">MOF</span></span>|<span data-ttu-id="63f34-124">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="63f34-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="63f34-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="63f34-125">Namespace</span></span>|<span data-ttu-id="63f34-126">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="63f34-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63f34-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f34-127">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
