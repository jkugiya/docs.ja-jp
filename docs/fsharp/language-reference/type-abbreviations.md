---
title: 型略称
description: コードを読みやすくするために、よりわかりやすい名前を型に付けるための F# 型略称について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630217"
---
# <a name="type-abbreviations"></a>型略称

*型略称* は、型の別名または代替名です。

## <a name="syntax"></a>構文

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>解説

コードを読みやすくするために、型略称を使用して、よりわかりやすい名前を型に付けることができます。 また、それらを使用して、本来記述するのが煩わい型に対して使いやすい名前を作成することもできます。さらに、型略称を使用して、基になる型を使用するすべてのコードを変更することなく、その型を変更しやすくすることもできます。 次に示すのは、簡易的な型略称です。

型略称のアクセシビリティは、既定で `public` に設定されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

次のコードのように、型略称にジェネリック パラメーターを含めることができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

前のコードで `Transform` は、任意の型の単一の引数を受け取り、同じ型の単一の値を返す関数を表す型略称です。

型略称は .NET Framework MSIL コードに保持されません。 そのため、別の .NET Framework 言語の F# アセンブリを使用する場合は、型略称に基になる型名を使用する必要があります。

型略称は、測定単位にも使用できます。 詳細については、「[測定単位](units-of-measure.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
