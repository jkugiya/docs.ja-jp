---
description: '詳細情報: SymmetricSecurityBindingElement'
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c158f0bedec91a74b305f359889dd307cff48079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715302"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="5b15b-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5b15b-103">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="5b15b-104">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5b15b-104">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b15b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5b15b-105">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5b15b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5b15b-106">Methods</span></span>  

 <span data-ttu-id="5b15b-107">SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="5b15b-107">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5b15b-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5b15b-108">Properties</span></span>  

 <span data-ttu-id="5b15b-109">SymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5b15b-109">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="5b15b-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="5b15b-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="5b15b-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="5b15b-111">Data type: string</span></span>  
  
 <span data-ttu-id="5b15b-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b15b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b15b-113">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="5b15b-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="5b15b-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="5b15b-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="5b15b-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="5b15b-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="5b15b-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="5b15b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b15b-117">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="5b15b-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b15b-118">要件</span><span class="sxs-lookup"><span data-stu-id="5b15b-118">Requirements</span></span>  
  
|<span data-ttu-id="5b15b-119">MOF</span><span class="sxs-lookup"><span data-stu-id="5b15b-119">MOF</span></span>|<span data-ttu-id="5b15b-120">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="5b15b-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5b15b-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="5b15b-121">Namespace</span></span>|<span data-ttu-id="5b15b-122">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="5b15b-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b15b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b15b-123">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
