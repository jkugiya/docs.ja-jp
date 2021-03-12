---
title: コンパイラのエラーと警告
description: F# コンパイラによって生成されるエラーと警告の説明と解決策
ms.date: 12/21/2019
ms.openlocfilehash: 9769ddee989f0774cfae8842e60dbd3fd2065f9c
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190178"
---
# <a name="f-compiler-messages"></a>F# コンパイラのメッセージ

このセクションでは、F# コンパイラが特定のコンストラクトに対して生成するコンパイラのエラーと警告について詳しく説明します。 既定のエラー セットは、次の方法で変更できます。

- `-warnaserror+` コンパイラ オプションを使用して、特定の警告をエラーとして扱う。

- `-nowarn` コンパイラ オプションを使用して特定の警告を無視する

このセクションに、特定の警告またはエラーがまだ記録されていない場合は、次を行います。

- このページの最後に移動し、エラーの番号またはテキストを含めてフィードバックを送信する、または
- 「[Create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx)」の手順に従って、このリポジトリの pull request を開いて、自分で追加する。

## <a name="see-also"></a>関連項目

- [F# コンパイラ オプション](../compiler-options.md)
