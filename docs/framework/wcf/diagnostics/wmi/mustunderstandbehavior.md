---
description: '詳細情報: 実行時の動作'
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 173548f2f3346a79bf7f53c90384db94a638a366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803127"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="c1717-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="c1717-103">MustUnderstandBehavior</span></span>

<span data-ttu-id="c1717-104">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="c1717-104">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1717-105">構文</span><span class="sxs-lookup"><span data-stu-id="c1717-105">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c1717-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1717-106">Methods</span></span>  

 <span data-ttu-id="c1717-107">MustUnderstandBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="c1717-107">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c1717-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c1717-108">Properties</span></span>  

 <span data-ttu-id="c1717-109">MustUnderstandBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c1717-109">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="c1717-110">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="c1717-110">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="c1717-111">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c1717-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1717-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c1717-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1717-113">`true` の場合、未処理の `MustUnderstand` 属性を持つすべての SOAP ヘッダーは、動作が例外をスローする原因となります。</span><span class="sxs-lookup"><span data-stu-id="c1717-113">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1717-114">要件</span><span class="sxs-lookup"><span data-stu-id="c1717-114">Requirements</span></span>  
  
|<span data-ttu-id="c1717-115">MOF</span><span class="sxs-lookup"><span data-stu-id="c1717-115">MOF</span></span>|<span data-ttu-id="c1717-116">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c1717-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c1717-117">名前空間</span><span class="sxs-lookup"><span data-stu-id="c1717-117">Namespace</span></span>|<span data-ttu-id="c1717-118">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c1717-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1717-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1717-119">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
