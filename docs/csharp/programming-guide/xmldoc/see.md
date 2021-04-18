---
title: <see> - C# プログラミング ガイド
description: XML <see> タグについて説明します。 このタグを使用すると、たとえば cref 属性を使用して、テキスト内からリンクを指定できます。
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 351dd2e4c7dbc76efa2edbed708fb342c553ce70
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494858"
---
# <a name="see-c-programming-guide"></a>\<see> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```csharp
/// <see cref="member"/>
// or
/// <see href="link">Link Text</see>
// or
/// <see langword="keyword"/>
```

## <a name="parameters"></a>パラメーター

- `cref="member"`

  現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。 *メンバー* は二重引用符 (" ") で囲む必要があります。

- `href="link"`

  特定の URL へのクリック可能なリンク。 たとえば、`<see href="https://github.com">GitHub</see>` によって生成されるクリック可能なリンクには、`https://github.com` にリンクされたテキスト :::no-loc text="GitHub"::: が含まれます。

- `langword="keyword"`

  `true` などの言語キーワード。

## <a name="remarks"></a>Remarks

`<see>` タグを使用すると、テキスト内からリンクを指定できます。 テキストが「関連項目」セクションに配置されていることを示すには、[\<seealso>](./seealso.md) を使用します。 コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](./cref-attribute.md)を使用します。 また、``href`` はハイパーリンクとして機能する有効な属性です。

コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。

次の例では、「概要」セクション内の `<see>` タグを示しています。

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
