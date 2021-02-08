---
title: アンセーフ コードとポインター - C# プログラミング ガイド
description: アンセーフ コードとポインターについて説明します。 C# ではポインターがサポートされていませんが、'unsafe' のキーワードでポインターを使用できる unsafe コンテキストを定義できます。
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 4d624bdc8fc4a756f47d66c9dec6eba8c24a9d9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782391"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="07258-104">アンセーフ コードとポインター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="07258-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="07258-105">タイプ セーフとセキュリティを維持するために、既定では C# はポインター演算をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="07258-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="07258-106">ただし、[unsafe](../../language-reference/keywords/unsafe.md) キーワードを使用すれば、ポインターを使用できる unsafe コンテキストを定義できます。</span><span class="sxs-lookup"><span data-stu-id="07258-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="07258-107">ポインターについて詳しくは、[ポインター型](pointer-types.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07258-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07258-108">共通言語ランタイム (CLR) では、アンセーフ コードは検査できないコードと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="07258-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="07258-109">C# のアンセーフ コードは、必ずしも危険ではありません。ただ、CLR で安全性を検査できないコードであるというだけです。</span><span class="sxs-lookup"><span data-stu-id="07258-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="07258-110">そのため CLR は、完全に信頼できるアセンブリ内にある場合にのみ、アンセーフ コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="07258-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="07258-111">アンセーフ コードを使用する場合は、セキュリティ上のリスクやポインター エラーが発生しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="07258-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="07258-112">アンセーフ コードの概要</span><span class="sxs-lookup"><span data-stu-id="07258-112">Unsafe code overview</span></span>

<span data-ttu-id="07258-113">アンセーフ コードには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="07258-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="07258-114">メソッド、型、およびコード ブロックをアンセーフとして定義できます。</span><span class="sxs-lookup"><span data-stu-id="07258-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="07258-115">アンセーフ コードでアプリケーションのパフォーマンスが向上することがあります。これは、配列のバインド チェックが削除されるためです。</span><span class="sxs-lookup"><span data-stu-id="07258-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="07258-116">アンセーフ コードは、ポインターを必要とするネイティブ関数を呼び出すときに必要です。</span><span class="sxs-lookup"><span data-stu-id="07258-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="07258-117">アンセーフ コードを使用すると、セキュリティと安定性の面でリスクが生じます。</span><span class="sxs-lookup"><span data-stu-id="07258-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="07258-118">unsafe ブロックを含むコードは、[-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを使ってコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="07258-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="07258-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="07258-119">Related sections</span></span>

<span data-ttu-id="07258-120">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="07258-120">For more information, see:</span></span>

- [<span data-ttu-id="07258-121">ポインター型</span><span class="sxs-lookup"><span data-stu-id="07258-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="07258-122">固定サイズ バッファー</span><span class="sxs-lookup"><span data-stu-id="07258-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="07258-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="07258-123">C# language specification</span></span>

<span data-ttu-id="07258-124">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の[アンセーフ コード](~/_csharplang/spec/unsafe-code.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="07258-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="07258-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="07258-125">See also</span></span>

- [<span data-ttu-id="07258-126">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="07258-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="07258-127">unsafe</span><span class="sxs-lookup"><span data-stu-id="07258-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
