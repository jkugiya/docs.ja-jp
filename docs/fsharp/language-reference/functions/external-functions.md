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
# <a name="external-functions"></a><span data-ttu-id="6077a-103">外部関数</span><span class="sxs-lookup"><span data-stu-id="6077a-103">External Functions</span></span>

<span data-ttu-id="6077a-104">このトピックでは、ネイティブ コードでの関数の呼び出しに関する F# 言語のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6077a-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="6077a-105">構文</span><span class="sxs-lookup"><span data-stu-id="6077a-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="6077a-106">解説</span><span class="sxs-lookup"><span data-stu-id="6077a-106">Remarks</span></span>

<span data-ttu-id="6077a-107">前の構文では、*arguments* は `System.Runtime.InteropServices.DllImportAttribute` 属性に指定される引数を表します。</span><span class="sxs-lookup"><span data-stu-id="6077a-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="6077a-108">最初の引数は、この関数を含む DLL の名前を表す文字列です。 .dll の拡張子は含めません。</span><span class="sxs-lookup"><span data-stu-id="6077a-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="6077a-109">呼び出し規則など、`System.Runtime.InteropServices.DllImportAttribute` クラスの任意のパブリック プロパティに対して追加の引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6077a-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="6077a-110">次のエクスポートされた関数を含むネイティブ C++ DLL があるとします。</span><span class="sxs-lookup"><span data-stu-id="6077a-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="6077a-111">次のコードを使用して、F# からこの関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6077a-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="6077a-112">ネイティブ コードとの相互運用性は "*プラットフォーム呼び出し*" と呼ばれ、CLR の機能です。</span><span class="sxs-lookup"><span data-stu-id="6077a-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="6077a-113">詳細については、「[アンマネージ コードとの相互運用](../../../framework/interop/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6077a-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="6077a-114">このセクションの情報は、F# に適用できます。</span><span class="sxs-lookup"><span data-stu-id="6077a-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="6077a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6077a-115">See also</span></span>

- [<span data-ttu-id="6077a-116">関数</span><span class="sxs-lookup"><span data-stu-id="6077a-116">Functions</span></span>](index.md)
