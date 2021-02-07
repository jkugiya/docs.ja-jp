---
description: '詳細情報: ServiceSecurityAuditBehavior'
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 5dfb3a70a80d5dea1ed360dcaf3a0db989bf671b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715471"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="8c879-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="8c879-103">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="8c879-104">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="8c879-104">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c879-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c879-105">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8c879-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c879-106">Methods</span></span>  

 <span data-ttu-id="8c879-107">ServiceSecurityAuditBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="8c879-107">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8c879-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c879-108">Properties</span></span>  

 <span data-ttu-id="8c879-109">ServiceSecurityAuditBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8c879-109">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="8c879-110">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="8c879-110">AuditLogLocation</span></span>  

 <span data-ttu-id="8c879-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8c879-111">Data type: string</span></span>  
  
 <span data-ttu-id="8c879-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c879-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c879-113">監査ログの場所。</span><span class="sxs-lookup"><span data-stu-id="8c879-113">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="8c879-114">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="8c879-114">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="8c879-115">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8c879-115">Data type: string</span></span>  
  
 <span data-ttu-id="8c879-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c879-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c879-117">監査イベントをログに記録するために使用されるメッセージ認証レベルの種類。</span><span class="sxs-lookup"><span data-stu-id="8c879-117">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="8c879-118">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="8c879-118">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="8c879-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="8c879-119">Data type: string</span></span>  
  
 <span data-ttu-id="8c879-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c879-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c879-121">監査ログに記録される承認イベントの種類。</span><span class="sxs-lookup"><span data-stu-id="8c879-121">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="8c879-122">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="8c879-122">SuppressAuditFailure</span></span>  

 <span data-ttu-id="8c879-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8c879-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="8c879-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8c879-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8c879-125">監査ログへの書き込みエラーを非表示にする動作を指定するブール型の値。</span><span class="sxs-lookup"><span data-stu-id="8c879-125">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c879-126">要件</span><span class="sxs-lookup"><span data-stu-id="8c879-126">Requirements</span></span>  
  
|<span data-ttu-id="8c879-127">MOF</span><span class="sxs-lookup"><span data-stu-id="8c879-127">MOF</span></span>|<span data-ttu-id="8c879-128">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8c879-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8c879-129">名前空間</span><span class="sxs-lookup"><span data-stu-id="8c879-129">Namespace</span></span>|<span data-ttu-id="8c879-130">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8c879-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c879-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c879-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
