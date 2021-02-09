---
description: '詳細情報: WriteOnly (Visual Basic)'
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 514a1de3c8c2cfbde6a9cffc5c235d92454dd966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674741"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="a8686-103">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8686-103">WriteOnly (Visual Basic)</span></span>

<span data-ttu-id="a8686-104">プロパティを書き込めるが、読み込みはできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a8686-104">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8686-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8686-105">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a8686-106">ルール</span><span class="sxs-lookup"><span data-stu-id="a8686-106">Rules</span></span>  

 <span data-ttu-id="a8686-107">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="a8686-107">**Declaration Context.**</span></span> <span data-ttu-id="a8686-108">`WriteOnly` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8686-108">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="a8686-109">つまり、`WriteOnly` プロパティの宣言コンテキストは、クラス、構造体、またはモジュールにする必要があり、ソース ファイル、名前空間、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a8686-109">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="a8686-110">プロパティは、変数ではなく `WriteOnly` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a8686-110">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="a8686-111">WriteOnly を使用するタイミング</span><span class="sxs-lookup"><span data-stu-id="a8686-111">When to Use WriteOnly</span></span>  

 <span data-ttu-id="a8686-112">場合によっては、使用しているコードで値を設定できても、それが何であるかを検出できないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8686-112">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="a8686-113">たとえば、社会登録番号やパスワードなどの機密データは、それが設定されていないコンポーネントからはアクセスできないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8686-113">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="a8686-114">このような場合は、`WriteOnly` プロパティを使用して値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a8686-114">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8686-115">`WriteOnly` プロパティを定義して使用する場合は、次の追加の保護対策を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a8686-115">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="a8686-116">**オーバーライド。**</span><span class="sxs-lookup"><span data-stu-id="a8686-116">**Overriding.**</span></span> <span data-ttu-id="a8686-117">プロパティがクラスのメンバーである場合は、既定値の [NotOverridable](notoverridable.md) に設定できます。`Overridable` または `MustOverride` としては宣言しないでください。</span><span class="sxs-lookup"><span data-stu-id="a8686-117">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="a8686-118">これにより、派生クラスがオーバーライドによって不要なアクセスを行うのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="a8686-118">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="a8686-119">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="a8686-119">**Access Level.**</span></span> <span data-ttu-id="a8686-120">プロパティの機密データを 1 つ以上の変数に保持する場合は、他のコードがアクセスできないように、[Private](private.md) として宣言してください。</span><span class="sxs-lookup"><span data-stu-id="a8686-120">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="a8686-121">**暗号化。**</span><span class="sxs-lookup"><span data-stu-id="a8686-121">**Encryption.**</span></span> <span data-ttu-id="a8686-122">すべての機密データを、プレーンテキストではなく暗号化された形式で保存します。</span><span class="sxs-lookup"><span data-stu-id="a8686-122">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="a8686-123">悪意のあるコードが何らかの方法でメモリ領域にアクセスできた場合は、そのデータを使用するのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="a8686-123">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="a8686-124">暗号化は、機密データをシリアル化する必要がある場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a8686-124">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="a8686-125">**リセット。**</span><span class="sxs-lookup"><span data-stu-id="a8686-125">**Resetting.**</span></span> <span data-ttu-id="a8686-126">プロパティを定義するクラス、構造体、またはモジュールが終了しているときに、機密データを既定値またはその他の意味のない値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="a8686-126">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="a8686-127">これにより、メモリの領域が一般的なアクセス用に解放されているときに、追加の保護が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a8686-127">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="a8686-128">**永続性。**</span><span class="sxs-lookup"><span data-stu-id="a8686-128">**Persistence.**</span></span> <span data-ttu-id="a8686-129">機密データは、ディスクなどにはなるべく保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="a8686-129">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="a8686-130">また、機密データをクリップボードに書き込まないでください。</span><span class="sxs-lookup"><span data-stu-id="a8686-130">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="a8686-131">`WriteOnly` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8686-131">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a8686-132">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="a8686-132">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8686-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8686-133">See also</span></span>

- [<span data-ttu-id="a8686-134">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="a8686-134">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="a8686-135">Private</span><span class="sxs-lookup"><span data-stu-id="a8686-135">Private</span></span>](private.md)
- [<span data-ttu-id="a8686-136">キーワード</span><span class="sxs-lookup"><span data-stu-id="a8686-136">Keywords</span></span>](../keywords/index.md)
