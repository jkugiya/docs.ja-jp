---
title: '方法: アセンブリの内容を表示する'
description: IL 逆アセンブラーを使用して、アセンブリの属性と、他のモジュールやアセンブリへの参照を表示できます。
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: c881abc3e88df4c1855a0faa29936621a4488078
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103044"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="de6be-103">方法: アセンブリの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="de6be-103">How to: View assembly contents</span></span>

<span data-ttu-id="de6be-104">[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用して、ファイル内の MSIL (Microsoft Intermediate Language) 情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="de6be-104">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="de6be-105">調べる対象のファイルがアセンブリの場合、この情報にはアセンブリの属性と他のモジュールやアセンブリへの参照が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="de6be-105">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="de6be-106">この情報は、ファイルがアセンブリまたはアセンブリの一部かどうか、およびファイルに他のモジュールまたはアセンブリへの参照があるかどうかを判断するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="de6be-106">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="de6be-107">*Ildasm.exe* を使用してアセンブリの内容を表示するには、コマンド プロンプトで「**ildasm \<assembly name>** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="de6be-107">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="de6be-108">たとえば、次のコマンドでは、*Hello.exe* アセンブリが逆アセンブルされます。</span><span class="sxs-lookup"><span data-stu-id="de6be-108">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="de6be-109">アセンブリ マニフェスト情報を表示するには、MSIL 逆アセンブラー ウィンドウで **[マニフェスト]** アイコンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="de6be-109">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="de6be-110">例</span><span class="sxs-lookup"><span data-stu-id="de6be-110">Example</span></span>

<span data-ttu-id="de6be-111">次の例では、基本の "Hello World" プログラムを使用します。</span><span class="sxs-lookup"><span data-stu-id="de6be-111">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="de6be-112">プログラムをコンパイルした後、*Ildasm.exe* を使用して *Hello.exe* アセンブリを逆アセンブルし、アセンブリ マニフェストを表示します。</span><span class="sxs-lookup"><span data-stu-id="de6be-112">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="de6be-113">*Hello.exe* アセンブリに対して *ildasm.exe* コマンドを実行し、MSIL 逆アセンブラー ウィンドウで **[マニフェスト]** アイコンをダブルクリックすると、次の内容が出力されます。</span><span class="sxs-lookup"><span data-stu-id="de6be-113">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="de6be-114">次の表では、例で使用した *Hello.exe* アセンブリのアセンブリ マニフェストにある各ディレクティブについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="de6be-114">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="de6be-115">ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="de6be-115">Directive</span></span>|<span data-ttu-id="de6be-116">説明</span><span class="sxs-lookup"><span data-stu-id="de6be-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="de6be-117">**.assembly extern \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="de6be-117">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="de6be-118">現在のモジュールによって参照される項目を含む別のアセンブリを指定します (この例では `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="de6be-118">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="de6be-119">**.publickeytoken \<token>**</span><span class="sxs-lookup"><span data-stu-id="de6be-119">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="de6be-120">参照されるアセンブリの実際のキーのトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-120">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="de6be-121">**.ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="de6be-121">**.ver \<version number>**</span></span>|<span data-ttu-id="de6be-122">参照されるアセンブリのバージョン番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-122">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="de6be-123">**.assembly \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="de6be-123">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="de6be-124">アセンブリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-124">Specifies the assembly name.</span></span>|
|<span data-ttu-id="de6be-125">**.hash algorithm \<int32 value>**</span><span class="sxs-lookup"><span data-stu-id="de6be-125">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="de6be-126">使用されるハッシュ アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-126">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="de6be-127">**.ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="de6be-127">**.ver \<version number>**</span></span>|<span data-ttu-id="de6be-128">アセンブリのバージョン番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-128">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="de6be-129">**.module \<file name>**</span><span class="sxs-lookup"><span data-stu-id="de6be-129">**.module \<file name>**</span></span>|<span data-ttu-id="de6be-130">アセンブリを構成するモジュールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-130">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="de6be-131">この例では、アセンブリは 1 つのファイルだけで構成されています。</span><span class="sxs-lookup"><span data-stu-id="de6be-131">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="de6be-132">**.subsystem \<value>**</span><span class="sxs-lookup"><span data-stu-id="de6be-132">**.subsystem \<value>**</span></span>|<span data-ttu-id="de6be-133">プログラムに必要なアプリケーション環境を指定します。</span><span class="sxs-lookup"><span data-stu-id="de6be-133">Specifies the application environment required for the program.</span></span> <span data-ttu-id="de6be-134">この例では、値 3 は、この実行可能ファイルがコンソールで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="de6be-134">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="de6be-135">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="de6be-135">**.corflags**</span></span>|<span data-ttu-id="de6be-136">現在メタデータ内で予約済みのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="de6be-136">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="de6be-137">アセンブリ マニフェストは、アセンブリの内容に応じて、多くの異なるディレクティブを格納できます。</span><span class="sxs-lookup"><span data-stu-id="de6be-137">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="de6be-138">アセンブリ マニフェストに含まれる多様なディレクティブの一覧については、ECMA のドキュメント、特に「Partition II: Metadata Definition and Semantics」(パーティション II: メタデータの定義とセマンティクス) および「Partition III:CIL Instruction Set」(パーティション III: CIL 命令セット) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de6be-138">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="de6be-139">ECMA の C# および共通言語基盤の標準</span><span class="sxs-lookup"><span data-stu-id="de6be-139">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="de6be-140">Standard ECMA-335 - 共通言語基盤 (CLI)</span><span class="sxs-lookup"><span data-stu-id="de6be-140">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/)

## <a name="see-also"></a><span data-ttu-id="de6be-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="de6be-141">See also</span></span>

- [<span data-ttu-id="de6be-142">アプリケーション ドメインとアセンブリ</span><span class="sxs-lookup"><span data-stu-id="de6be-142">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="de6be-143">アプリケーション ドメインとアセンブリに関する方法のトピック</span><span class="sxs-lookup"><span data-stu-id="de6be-143">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="de6be-144">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="de6be-144">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
