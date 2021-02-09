---
description: '詳細情報: GetType 演算子 (Visual Basic)'
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 15fe9c28997aa01527f23c0cc8fdbb0fe6cc53f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665992"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="1405a-103">GetType 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1405a-103">GetType Operator (Visual Basic)</span></span>

<span data-ttu-id="1405a-104">指定した型の <xref:System.Type> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1405a-104">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="1405a-105"><xref:System.Type> オブジェクトは、そのプロパティ、メソッド、イベントなど、型に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1405a-105">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1405a-106">構文</span><span class="sxs-lookup"><span data-stu-id="1405a-106">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1405a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1405a-107">Parameters</span></span>  
  
|<span data-ttu-id="1405a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1405a-108">Parameter</span></span>|<span data-ttu-id="1405a-109">説明</span><span class="sxs-lookup"><span data-stu-id="1405a-109">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="1405a-110">情報を必要とする型の名前。</span><span class="sxs-lookup"><span data-stu-id="1405a-110">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1405a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="1405a-111">Remarks</span></span>  

 <span data-ttu-id="1405a-112">`GetType` 演算子は、指定された `typename` の <xref:System.Type> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1405a-112">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="1405a-113">定義された型の名前を `typename` で渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1405a-113">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="1405a-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1405a-114">This includes the following:</span></span>  
  
- <span data-ttu-id="1405a-115">Visual Basic の任意のデータ型 (`Boolean` や `Date` など)。</span><span class="sxs-lookup"><span data-stu-id="1405a-115">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="1405a-116">.NET Framework の任意のクラス、構造体、モジュール、インターフェイス (<xref:System.ArgumentException?displayProperty=nameWithType> や <xref:System.Double?displayProperty=nameWithType> など)。</span><span class="sxs-lookup"><span data-stu-id="1405a-116">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1405a-117">アプリケーションで定義されている任意のクラス、構造体、モジュール、インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="1405a-117">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="1405a-118">アプリケーションで定義されている任意の配列。</span><span class="sxs-lookup"><span data-stu-id="1405a-118">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="1405a-119">アプリケーションで定義されている任意のデリゲート。</span><span class="sxs-lookup"><span data-stu-id="1405a-119">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="1405a-120">Visual Basic、.NET Framework、お使いのアプリケーションによって定義された任意の列挙型。</span><span class="sxs-lookup"><span data-stu-id="1405a-120">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="1405a-121">オブジェクト変数の型オブジェクトを取得する場合は、<xref:System.Type.GetType%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1405a-121">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1405a-122">`GetType` 演算子は、次のような場合に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="1405a-122">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="1405a-123">実行時に型のメタデータにアクセスする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="1405a-123">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="1405a-124"><xref:System.Type> オブジェクトは、型のメンバーやデプロイ情報などのメタデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="1405a-124">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="1405a-125">これは、たとえば、アセンブリについて検討するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="1405a-125">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="1405a-126">詳細については、「<xref:System.Reflection?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1405a-126">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1405a-127">2 つのオブジェクト参照を比較して、それらが同じ型のインスタンスを参照しているかどうかを確認する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="1405a-127">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="1405a-128">そうである場合、`GetType` は同じ <xref:System.Type> オブジェクトへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="1405a-128">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1405a-129">例</span><span class="sxs-lookup"><span data-stu-id="1405a-129">Example</span></span>  

 <span data-ttu-id="1405a-130">`GetType` 演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1405a-130">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="1405a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="1405a-131">See also</span></span>

- [<span data-ttu-id="1405a-132">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="1405a-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1405a-133">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="1405a-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1405a-134">演算子および式</span><span class="sxs-lookup"><span data-stu-id="1405a-134">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
