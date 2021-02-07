---
description: 詳細については、VisualStudio を参照してください。.ctor
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 1a1b436c2b15fdf07f924aa0db2a13598422e988
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739990"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="09100-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="09100-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>

<span data-ttu-id="09100-104">[VisualStudio](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)クラスのインスタンスを作成します。このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="09100-104">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09100-105">構文</span><span class="sxs-lookup"><span data-stu-id="09100-105">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09100-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09100-106">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="09100-107">パラメーター値</span><span class="sxs-lookup"><span data-stu-id="09100-107">Parameter Values</span></span>  

 <span data-ttu-id="09100-108">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="09100-108">*operationDescription*</span></span>  
  
 <span data-ttu-id="09100-109">操作名、戻り値の型、パラメーター情報など、生成されるワークフロー アクティビティで実行される操作を記述します。</span><span class="sxs-lookup"><span data-stu-id="09100-109">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="09100-110">このパラメーターの値を **null** にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="09100-110">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="09100-111">これは、メッセージ コントラクトを使用し、1 つのメッセージと共に引数を受け取る同期操作を示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="09100-111">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="09100-112">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="09100-112">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="09100-113">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="09100-113">*configurationName*</span></span>  
  
 <span data-ttu-id="09100-114">エンドポイント構成名を指定します。</span><span class="sxs-lookup"><span data-stu-id="09100-114">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="09100-115">このパラメーターの値を **null** または空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="09100-115">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="09100-116">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="09100-116">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="09100-117">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="09100-117">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="09100-118">操作のサービスの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="09100-118">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="09100-119">このパラメーターの値を **null** または空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="09100-119">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="09100-120">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="09100-120">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09100-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="09100-121">See also</span></span>

- [<span data-ttu-id="09100-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="09100-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
