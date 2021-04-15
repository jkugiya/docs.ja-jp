---
description: コンパイラ出力を制御する C# コンパイラ オプション。 これらのオプションは、コンパイルからのアセンブリの生成を制御します。
title: C# コンパイラ オプション - 出力オプション
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- DocumentationFile compiler option [C#]
- OutputAssembly compiler option [C#]
- PlatformTarget compiler option [C#]
- ProduceReferenceAssembly compiler option [C#]
- TargetType compiler option [C#]
ms.openlocfilehash: 9caa290a7c9b5fea1b0f896e9443075b4b470f7b
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636845"
---
# <a name="c-compiler-options-that-control-compiler-output"></a>コンパイラ出力を制御する C# コンパイラ オプション

以下のオプションは、コンパイラ出力の生成を制御します。 新しい MSBuild 構文は、**太字** で示されています。 以前の *csc.exe* 構文は、`code style` で示されています。

- **DocumentationFile** / `-doc`: `///` コメントから XML ドキュメント ファイルを生成します。
- **OutputAssembly** / `-out`: 出力アセンブリ ファイルを指定します。
- **PlatformTarget** / `-platform`: ターゲット プラットフォームの CPU を指定します。
- **ProduceReferenceAssembly** / `-refout`: 参照アセンブリを生成します。
- **TargetType** `-target`: 出力アセンブリの種類を指定します。

## <a name="documentationfile"></a>DocumentationFile

**DocumentationFile** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。 コードのドキュメントの作成の詳細については、「[ドキュメント コメント用の推奨タグ](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。 値は、出力 XML ファイルへのパスを指定します。 この XML ファイルには、コンパイルのソース コード ファイル内のコメントが含まれています。

```xml
<DocumentationFile>path/to/file.xml</DocumentationFile>
```

Main ステートメントまたは最上位レベルのステートメントを含むソース コード ファイルは、最初に XML に出力されます。 生成された .xml ファイルを [IntelliSense](/visualstudio/ide/using-intellisense) で使用することがよくあります。 *.xml* ファイル名は、アセンブリ名と同じである必要があります。 *.xml* ファイルは、アセンブリと同じディレクトリに存在する必要があります。 アセンブリが Visual Studio プロジェクトで参照されると、 *.xml* ファイルも同様に検出されます。 コード コメントの生成の詳細については、[コード コメントの追加](/visualstudio/ide/reference/generate-xml-documentation-comments)に関するページを参照してください。 [`<TargetType:Module>`](#targettype) でコンパイルしない限り、`file` には `<assembly>` タグと `</assembly>` タグが追加されます。これにより、出力ファイルのアセンブリ マニフェストを含むファイルの名前が指定されます。 例については、「[XML ドキュメント機能を使用する方法](../../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)」を参照してください。

> [!NOTE]
> **DocumentationFile** オプションは、プロジェクト内のすべてのファイルに適用されます。 特定のファイルまたはコードの特定のセクションについて、ドキュメントのコメントに関する警告を無効にするには、[#pragma warning](../preprocessor-directives.md#pragma-warning) を使用します。

## <a name="outputassembly"></a>OutputAssembly

**OutputAssembly** オプションは、出力ファイルの名前を指定します。 出力パスには、コンパイラ出力が配置されるフォルダーを指定します。

```xml
<OutputAssembly>folder</OutputAssembly>
```

作成するファイルの完全な名前と拡張子を指定します。 出力ファイルの名前を指定しない場合、MSBuild ではプロジェクトの名前を使用して出力アセンブリの名前を指定します。 古いスタイルのプロジェクトでは、次のルールを使用します。

- .exe は `Main` メソッドまたは最上位レベルのステートメントを含むソース コード ファイルからその名前を取得します。  
- .dll または .netmodule は最初のソース コード ファイルからその名前を取得します。

コンパイルの一部として生成されるすべてのモジュールが、同じくコンパイルで作成されるアセンブリに関連付けらるファイルになります。 [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ マニフェストを表示し、関連付けられているファイルを確認します。

exe を [フレンド アセンブリ](../../../standard/assembly/friend.md)のターゲットにするには、**OutputAssembly** コンパイラ オプションが必要です。

## <a name="platformtarget"></a>PlatformTarget

アセンブリを実行できる CLR のバージョンを指定します。

```xml
<PlatformTarget>anycpu</PlatformTarget>
```

- **anycpu** (既定) は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。 可能な場合は、アプリケーションを 64 ビット プロセスとして実行し、32 ビット モードしか使用できない場合は、32 ビットにフォールバックします。
- **anycpu32bitpreferred** は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。 64 ビットと 32 ビットの両方のアプリケーションをサポートするシステムで、32 ビット モードでアプリケーションを実行します。 このオプションは、.NET Framework 4.5 以降を対象とするプロジェクトに対してのみ指定できます。
- **ARM** は、Advanced RISC Machine (ARM) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。
- **ARM64** では、A64 命令セットをサポートする Advanced RISC Machine (ARM) プロセッサが搭載されたコンピューター上で 64 ビット CLR によって実行されるように、アセンブリがコンパイルされます。
- **x64** は AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。
- **x86** は 32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。
- **Itanium** は、Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。

64 ビット Windows オペレーティング システムの場合:

- **x86** でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。
- **anycpu** でコンパイルでされた DLL は、読み込み先のプロセスと同じ CLR で実行されます。
- **anycpu** でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。
- **anycpu32bitpreferred** でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。

**anycpu32bitpreferred** 設定は、実行可能 (.EXE) ファイルに対してのみ有効であり、.NET Framework 4.5 以降が必要です。 Windows 64 ビット オペレーティング システムで実行するアプリケーションの開発に関する詳細は、「[64 ビット アプリケーション](../../../framework/64-bit-apps.md)」を参照してください。

**PlatformTarget** オプションは、Visual Studio でプロジェクトの **[ビルド]** プロパティ ページから設定します。

.NET Core と .NET 5 以降のリリースでは、**anycpu** の動作にいくつかの微妙な違いがあります。 **anycpu** を設定したら、アプリを発行し、x86 `dotnet.exe` または x64 `dotnet.exe` で実行します。 自己完結型アプリの場合、`dotnet publish` の手順によって、RID 構成用の実行可能ファイルがパッケージ化されます。

## <a name="producereferenceassembly"></a>ProduceReferenceAssembly

**ProduceReferenceAssembly** オプションは、参照アセンブリを出力するファイル パスを指定します。 Emit API では、これを `metadataPeStream` に変換します。 `filepath` は、参照アセンブリのパスを指定します。 通常はプライマリ アセンブリのファイルパスと一致します。 (MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブフォルダー内に参照アセンブリを配置することです。

```xml
<ProduceReferenceAssembly>filepath</ProduceReferenceAssembly>
```

参照アセンブリは、ライブラリのパブリック API サーフェイスを表すために必要最小限のメタデータのみを含む特殊なアセンブリです。 これには、ビルド ツールでアセンブリを参照するときに重要なすべてのメンバーの宣言が含まれます。 参照アセンブリでは、すべてのメンバーの実装とプライベート メンバーの宣言が除外されます。 このようなメンバーが API コントラクトに影響を与えることはありません。 詳細については、.NET のガイドの「[参照アセンブリ](../../../standard/assembly/reference-assemblies.md)」を参照してください。

**ProduceReferenceAssembly** オプションと [**ProduceOnlyReferenceAssembly**](./code-generation.md#produceonlyreferenceassembly) オプションは同時に指定できません。

## <a name="targettype"></a>TargetType

**TargetType** コンパイラ オプションは、次のいずれかの形式で指定できます。  
  
- **library**: コード ライブラリを作成する場合。 **library** は既定値です。
- **exe**: .exe ファイルを作成する場合。  
- **module**: モジュールを作成する場合。  
- **winexe**: Windows プログラムを作成する場合。
- **winmdobj**: *.winmdobj* 中間ファイルを作成する場合。
- **appcontainerexe**: Windows 8.x Store アプリの .exe ファイルを作成する場合。
  
> [!NOTE]
> .NET Framework ターゲットの場合は、**module** を指定しない限り、このオプションを使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに配置されます。 詳細については、「[.NET のアセンブリ](../../../standard/assembly/index.md)」と「[共通の属性](../attributes/global.md)」を参照してください。

```xml
<TargetType>library</TargetType>
```

コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。 コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。 コマンド ラインで複数の出力ファイルを生成する場合は、アセンブリ マニフェストを 1 つだけ作成できます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。

アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。

### <a name="library"></a>ライブラリ

**library** オプションを指定した場合、コンパイラは実行可能ファイル (EXE) ではなく、ダイナミックリンク ライブラリ (DLL) を作成します。 *.dll* 拡張子の DLL が作成されます。 [**OutputAssembly**](#outputassembly) オプションを特に指定しない限り、出力ファイル名は最初の入力ファイルと同じになります。 *.dll* ファイルを作成する際に、[`Main`](../../programming-guide/main-and-command-args/index.md) メソッドは必要ありません。

### <a name="exe"></a>exe

**exe** オプションを指定した場合、コンパイラは実行可能な (EXE) コンソール アプリケーションを作成します。 実行可能ファイルは、.exe という拡張子で作成されます。 Windows プログラムの実行可能ファイルを作成する場合は、**winexe** を使用します。 [**OutputAssembly**](#outputassembly) オプションで指定しない限り、出力ファイル名はエントリ ポイント ([Main](../../programming-guide/main-and-command-args/index.md) メソッドまたは最上位レベルのステートメント) を含む入力ファイルと同じになります。 エントリ ポイントは、.exe ファイルにコンパイルされるソース コード ファイル内に 1 つだけ必要です。 コードに `Main` メソッドを含むクラスが複数ある場合は、[**StartupObject**](./advanced.md#mainentrypoint-or-startupobject) コンパイラ オプションを使用して、`Main` メソッドを含めるクラスを指定できます。  

### <a name="module"></a>name

このオプションでは、コンパイラはアセンブリ マニフェストを生成しません。 既定では、このオプションを使用してコンパイルすることによって作成された出力ファイルに、 *.netmodule* という拡張子が付きます。 アセンブリ マニフェストのないファイルは、.NET ランタイムによって読み込むことができません。 ただし、このようなファイルは、[**AddModules**](inputs.md#addmodules) を使用して、アセンブリのアセンブリ マニフェストに組み込むことができます。 複数のモジュールが 1 回のコンパイルで作成される場合、あるモジュールの [internal](../keywords/internal.md) 型をコンパイル中に別のモジュールで使用することができます。 あるモジュールのコードが別のモジュールの `internal` 型を参照する場合は、[**AddModules**](inputs.md#addmodules) を使用して、両方のモジュールをアセンブリ マニフェストに組み込む必要があります。 Visual Studio 開発環境では、モジュールの作成はサポートされていません。

### <a name="winexe"></a>winexe

**winexe** オプションを使用すると、実行可能な (EXE) Windows プログラムがコンパイラによって作成されます。 実行可能ファイルは、.exe という拡張子で作成されます。 Windows プログラムは、.NET ライブラリまたは Windows API のユーザー インターフェイスを提供するプログラムです。 コンソール アプリケーションを作成するには、**exe** を使用します。 [**OutputAssembly**](#outputassembly) オプションで指定しない限り、出力ファイル名は [`Main`](../../programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。 `Main` メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。 コードに `Main` メソッドを含むクラスが複数ある場合は、[**StartupObject**](./advanced.md#mainentrypoint-or-startupobject) オプションを使用して、`Main` メソッドを含めるクラスを指定できます。

### <a name="winmdobj"></a>winmdobj

**winmdobj** オプションを使用すると、コンパイラは、Windows ランタイム バイナリ ファイル ( *.winmd*) に変換できる *.winmdobj* 中間ファイルを作成します。 *.winmd* ファイルは、マネージド言語プログラムだけでなく JavaScript および C++ プログラムでも使用できます。

**winmdobj** 設定は、中間モジュールが必要であることをコンパイラに通知します。 *.winmdobj* ファイルは <xref:Microsoft.Build.Tasks.WinMDExp> エクスポート ツールで送信され、Windows メタデータ ファイル ( *.winmd*) が生成されます。 *.winmd* ファイルには、元のライブラリのコードと WinMD メタデータの両方が含まれています。メタデータは、JavaScript または C++、および Windows ランタイムで使用されます。 **winmdobj** コンパイラ オプションを使用してコンパイルされたファイルの出力は、WimMDExp エクスポート ツール用の入力としてのみ使用されます。 *.winmdobj* ファイル自体は直接参照されません。 [**OutputAssembly**](#outputassembly) オプションを使用しない限り、出力ファイル名は最初の入力ファイルと同じになります。 [`Main`](../../programming-guide/main-and-command-args/index.md) メソッドは必要ありません。

### <a name="appcontainerexe"></a>appcontainerexe

**appcontainerexe** コンパイラ オプションを使用すると、アプリケーション コンテナーで実行する必要のある Windows 実行可能ファイル ( *.exe*) がコンパイラによって作成されます。 このオプションは [-target:winexe](output.md) に相当しますが、Windows 8.x Store アプリ用に設計されています。

アプリケーション コンテナーでのアプリケーションの実行を要求するために、このオプションは、[Portable Executable](/windows/desktop/Debug/pe-format) (PE) ファイルでビットを設定します。 このビットが設定されている場合、CreateProcess メソッドがアプリケーション コンテナー外の実行可能ファイルを起動しようとすると、エラーが発生します。 [**OutputAssembly**](#outputassembly) オプションを使用しない限り、出力ファイル名は [`Main`](../../programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。
