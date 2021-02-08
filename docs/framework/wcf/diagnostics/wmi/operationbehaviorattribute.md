---
description: '詳細情報: OperationBehaviorAttribute'
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: c1f1b80134163ee65d5015e52017f5bb455aeac7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803062"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="0ce5f-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0ce5f-103">OperationBehaviorAttribute</span></span>

<span data-ttu-id="0ce5f-104">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0ce5f-104">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce5f-105">構文</span><span class="sxs-lookup"><span data-stu-id="0ce5f-105">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0ce5f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0ce5f-106">Methods</span></span>  

 <span data-ttu-id="0ce5f-107">OperationBehaviorAttribute クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-107">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0ce5f-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0ce5f-108">Properties</span></span>  

 <span data-ttu-id="0ce5f-109">OperationBehaviorAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-109">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="0ce5f-110">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="0ce5f-110">AutoDisposeParameters</span></span>  

 <span data-ttu-id="0ce5f-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="0ce5f-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="0ce5f-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0ce5f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ce5f-113">パラメーターの自動破棄機能の状態です。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-113">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="0ce5f-114">偽装</span><span class="sxs-lookup"><span data-stu-id="0ce5f-114">Impersonation</span></span>  

 <span data-ttu-id="0ce5f-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="0ce5f-115">Data type: string</span></span>  
  
 <span data-ttu-id="0ce5f-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0ce5f-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ce5f-117">操作がサポートする、呼び出し元の偽装レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-117">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="0ce5f-118">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="0ce5f-118">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="0ce5f-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="0ce5f-119">Data type: string</span></span>  
  
 <span data-ttu-id="0ce5f-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0ce5f-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ce5f-121">操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-121">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="0ce5f-122">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="0ce5f-122">TransactionAutoComplete</span></span>  

 <span data-ttu-id="0ce5f-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="0ce5f-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="0ce5f-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0ce5f-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ce5f-125">未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-125">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="0ce5f-126">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="0ce5f-126">TransactionScopeRequired</span></span>  

 <span data-ttu-id="0ce5f-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="0ce5f-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="0ce5f-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="0ce5f-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ce5f-129">操作がトランザクションを必要とするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-129">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce5f-130">要件</span><span class="sxs-lookup"><span data-stu-id="0ce5f-130">Requirements</span></span>  
  
|<span data-ttu-id="0ce5f-131">MOF</span><span class="sxs-lookup"><span data-stu-id="0ce5f-131">MOF</span></span>|<span data-ttu-id="0ce5f-132">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="0ce5f-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0ce5f-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="0ce5f-133">Namespace</span></span>|<span data-ttu-id="0ce5f-134">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="0ce5f-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ce5f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ce5f-135">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
