---
description: '詳細情報: アンマネージド コードでの相互運用例外の処理'
title: 例外の相互運用性
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 3062aea2632771605c5a3c942c8471309e043f60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713196"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>アンマネージド コードでの相互運用例外の処理

アンマネージド コードの例外の相互運用は、Windows プラットフォームでのみサポートされています。 Windows 以外のプラットフォームでは移植性の問題が発生します。 Unix ABI には例外処理の定義がないため、マネージド コードでは、内部での例外メカニズムのしくみが認識されません。 そのため、例外が発生すると、予期しない動作やクラッシュが発生する可能性があります。

## <a name="setjmplongjmp-behaviors"></a>Setjmp と Longjmp の動作

`setjmp` および `longjmp` C 関数との相互運用はサポートされていません。 `longjmp` を使用して、マネージド フレームをスキップすることはできません。

詳しくは、[longjmp のドキュメント](/cpp/c-runtime-library/reference/longjmp)を参照してください。

## <a name="see-also"></a>関連項目

- [例外](index.md)
- [ネイティブ ライブラリとの相互運用](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
