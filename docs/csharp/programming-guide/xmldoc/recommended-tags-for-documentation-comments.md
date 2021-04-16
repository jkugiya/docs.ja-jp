---
title: ドキュメント コメント用の推奨タグ - C# プログラミング ガイド
description: ドキュメント コメント用の推奨タグについて説明します。 推奨タグの一覧を参照し、使用可能なその他のリソースを確認します。
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 74fd18a09458c399aa135552e5f6f0bca359f09e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477836"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="67616-104">ドキュメント コメント用の推奨タグ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="67616-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="67616-105">コード内のドキュメント コメントは、C# コンパイラによって処理され、 **/doc** コマンド ライン オプションで指定した名前のファイルに XML 形式で出力されます。</span><span class="sxs-lookup"><span data-stu-id="67616-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="67616-106">コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[DocFX](https://dotnet.github.io/docfx/) や [Sandcastle](https://github.com/EWSoftware/SHFB) などのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="67616-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="67616-107">タグは、型や型メンバーなどのコード コンストラクターに対して処理されます。</span><span class="sxs-lookup"><span data-stu-id="67616-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="67616-108">ドキュメント コメントは、名前空間に適用できません。</span><span class="sxs-lookup"><span data-stu-id="67616-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="67616-109">コンパイラは、有効な XML のタグをすべて処理します。</span><span class="sxs-lookup"><span data-stu-id="67616-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="67616-110">ユーザー ドキュメントで一般的に使用される機能を提供するタグを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="67616-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="67616-111">Tags</span><span class="sxs-lookup"><span data-stu-id="67616-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="67616-112">(\* は、コンパイラによって構文が検証されることを示します。)</span><span class="sxs-lookup"><span data-stu-id="67616-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="67616-113">ドキュメント コメントのテキストに山かっこを表示する場合は、`<` と `>` の HTML エンコードを使用します。これはそれぞれ、`&lt;` と `&gt;` になります。</span><span class="sxs-lookup"><span data-stu-id="67616-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="67616-114">このエンコードは次の例に示されています。</span><span class="sxs-lookup"><span data-stu-id="67616-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="67616-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="67616-115">See also</span></span>

- [<span data-ttu-id="67616-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="67616-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="67616-117">**DocumentationFile** (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="67616-117">**DocumentationFile** (C# compiler options)</span></span>](../../language-reference/compiler-options/output.md#documentationfile)
- [<span data-ttu-id="67616-118">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="67616-118">XML documentation comments</span></span>](./index.md)
