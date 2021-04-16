---
title: ソース行、ファイル、およびパスの識別子
description: コード内でソースの行番号、ディレクトリ、ファイル名にアクセスできるようにする F# の組み込み識別子の値の使用方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216751"
---
# <a name="source-line-file-and-path-identifiers"></a>ソース行、ファイル、およびパスの識別子

`__LINE__`、`__SOURCE_DIRECTORY__`、`__SOURCE_FILE__` の識別子は、コード内でソースの行番号、ディレクトリ、ファイル名にアクセスできるようにする組み込みの値です。

## <a name="syntax"></a>構文

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>解説

これらの各値には型 `string` が指定されています。

次の表は、F# で使用できるソース行、ファイル、パスの識別子をまとめたものです。 これらの識別子はプリプロセッサ マクロではなく、コンパイラによって認識される組み込みの値です。

|定義済み識別子|説明|
|---------------------|-----------|
|`__LINE__`|`#line` ディレクティブを考慮して、現在の行番号として評価されます。|
|`__SOURCE_DIRECTORY__`|`#line` ディレクティブを考慮して、ソース ディレクトリの現在の完全なパスとして評価されます。|
|`__SOURCE_FILE__`|`#line` ディレクティブを考慮して、パスを除いた現在のソース ファイル名として評価されます。|

`#line` ディレクティブの詳細については、「[コンパイラ ディレクティブ](compiler-directives.md)」を参照してください。

## <a name="example"></a>例

これらの値の使用方法を次のコード例に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

出力:

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>関連項目

- [コンパイラ ディレクティブ](compiler-directives.md)
- [F# 言語リファレンス](index.md)
