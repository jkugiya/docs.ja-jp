---
description: 詳細については、「CustomBindingElement」を参照してください。
title: CustomBindingElement
ms.date: 03/30/2017
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
ms.openlocfilehash: fc3f1fcbfc54ff082f87e04a894226ff9ca996bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757515"
---
# <a name="custombindingelement"></a><span data-ttu-id="e0956-103">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="e0956-103">CustomBindingElement</span></span>

<span data-ttu-id="e0956-104">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="e0956-104">CustomBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0956-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0956-105">Syntax</span></span>  
  
```csharp
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e0956-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e0956-106">Methods</span></span>  

 <span data-ttu-id="e0956-107">CustomBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="e0956-107">The CustomBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0956-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e0956-108">Properties</span></span>  

 <span data-ttu-id="e0956-109">CustomBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e0956-109">The CustomBindingElement class has the following property:</span></span>  
  
### <a name="name"></a><span data-ttu-id="e0956-110">名前</span><span class="sxs-lookup"><span data-stu-id="e0956-110">Name</span></span>  

 <span data-ttu-id="e0956-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="e0956-111">Data type: string</span></span>  
  
 <span data-ttu-id="e0956-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e0956-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0956-113">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="e0956-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e0956-114">この値は、カスタム バインディングの識別文字列として機能するユーザー定義文字列です。</span><span class="sxs-lookup"><span data-stu-id="e0956-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0956-115">要件</span><span class="sxs-lookup"><span data-stu-id="e0956-115">Requirements</span></span>  
  
|<span data-ttu-id="e0956-116">MOF</span><span class="sxs-lookup"><span data-stu-id="e0956-116">MOF</span></span>|<span data-ttu-id="e0956-117">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e0956-117">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e0956-118">名前空間</span><span class="sxs-lookup"><span data-stu-id="e0956-118">Namespace</span></span>|<span data-ttu-id="e0956-119">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e0956-119">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0956-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0956-120">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
