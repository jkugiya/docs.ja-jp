---
description: '詳細情報: AsymmetricSecurityBindingElement'
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 25d0ac205491e9ce27c59d3a0670d1e4a3150e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757944"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="795f7-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="795f7-103">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="795f7-104">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="795f7-104">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="795f7-105">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="795f7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="795f7-106">Methods</span></span>  

 <span data-ttu-id="795f7-107">AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="795f7-107">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="795f7-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="795f7-108">Properties</span></span>  

 <span data-ttu-id="795f7-109">AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="795f7-109">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="795f7-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="795f7-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="795f7-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="795f7-111">Data type: string</span></span>  
  
 <span data-ttu-id="795f7-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="795f7-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="795f7-113">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="795f7-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="795f7-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="795f7-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="795f7-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="795f7-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="795f7-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="795f7-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="795f7-117">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="795f7-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795f7-118">要件</span><span class="sxs-lookup"><span data-stu-id="795f7-118">Requirements</span></span>  
  
|<span data-ttu-id="795f7-119">MOF</span><span class="sxs-lookup"><span data-stu-id="795f7-119">MOF</span></span>|<span data-ttu-id="795f7-120">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="795f7-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="795f7-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="795f7-121">Namespace</span></span>|<span data-ttu-id="795f7-122">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="795f7-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="795f7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="795f7-123">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
