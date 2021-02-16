---
description: '詳細情報: 方法:Windows API を呼び出す (Visual Basic)'
title: '方法: Windows API を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: ec25df3715b1f8a4612c1575b5f7192d0a133c4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464912"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="ac305-103">方法: Windows API を呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac305-103">How to: Call Windows APIs (Visual Basic)</span></span>

<span data-ttu-id="ac305-104">この例では、`MessageBox` 関数を user32.dll に定義して呼び出し、文字列を関数に渡します。</span><span class="sxs-lookup"><span data-stu-id="ac305-104">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac305-105">例</span><span class="sxs-lookup"><span data-stu-id="ac305-105">Example</span></span>  

 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="ac305-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ac305-106">Compile the code</span></span>  

 <span data-ttu-id="ac305-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac305-107">This example requires:</span></span>  
  
- <span data-ttu-id="ac305-108"><xref:System> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="ac305-108">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ac305-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="ac305-109">Robust Programming</span></span>  

 <span data-ttu-id="ac305-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac305-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ac305-111">メソッドが静的ではない、抽象である、または以前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="ac305-111">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="ac305-112">親の型がインターフェイスであるか、*name* または *dllName* の長さが 0 です。</span><span class="sxs-lookup"><span data-stu-id="ac305-112">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="ac305-113">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="ac305-113">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="ac305-114">*name* または *dllName* が `Nothing` です。</span><span class="sxs-lookup"><span data-stu-id="ac305-114">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="ac305-115">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="ac305-115">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="ac305-116">含んでいる型が `CreateType` を使用して以前に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ac305-116">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="ac305-117">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="ac305-117">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac305-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac305-118">See also</span></span>

- [<span data-ttu-id="ac305-119">プラットフォーム呼び出しの詳細</span><span class="sxs-lookup"><span data-stu-id="ac305-119">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="ac305-120">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="ac305-120">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="ac305-121">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="ac305-121">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="ac305-122">[リフレクション出力によるメソッドの定義](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac305-122">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="ac305-123">チュートリアル: Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="ac305-123">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="ac305-124">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="ac305-124">COM Interop</span></span>](index.md)
