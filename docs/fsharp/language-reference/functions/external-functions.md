---
title: 外部関数
description: ネイティブ コードでの関数の呼び出しに関する F# 言語のサポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968729"
---
# <a name="external-functions"></a>外部関数

このトピックでは、ネイティブ コードでの関数の呼び出しに関する F# 言語のサポートについて説明します。

## <a name="syntax"></a>構文

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>解説

前の構文では、*arguments* は `System.Runtime.InteropServices.DllImportAttribute` 属性に指定される引数を表します。 最初の引数は、この関数を含む DLL の名前を表す文字列です。 .dll の拡張子は含めません。 呼び出し規則など、`System.Runtime.InteropServices.DllImportAttribute` クラスの任意のパブリック プロパティに対して追加の引数を指定できます。

次のエクスポートされた関数を含むネイティブ C++ DLL があるとします。

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

次のコードを使用して、F# からこの関数を呼び出すことができます。

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

ネイティブ コードとの相互運用性は "*プラットフォーム呼び出し*" と呼ばれ、CLR の機能です。 詳細については、「[アンマネージ コードとの相互運用](../../../framework/interop/index.md)」を参照してください。 このセクションの情報は、F# に適用できます。

## <a name="see-also"></a>関連項目

- [関数](index.md)
