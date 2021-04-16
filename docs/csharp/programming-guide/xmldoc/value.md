---
title: <value> - C# プログラミング ガイド
description: XML タグについて説明 <value> します。 このタグを使用すると、プロパティが表す値を記述することができます。
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477645"
---
# <a name="value-c-programming-guide"></a>\<value> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```xml
<value>property-description</value>
```

## <a name="parameters"></a>パラメーター

- `property-description`

  プロパティの説明。

## <a name="remarks"></a>Remarks

`<value>` タグを使用して、プロパティが表す値を記述することができます。 Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](./summary.md) タグが追加されます。 その後、手動で `<value>` タグを追加してプロパティが表す値を記述する必要があります。

コンパイル時に [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
