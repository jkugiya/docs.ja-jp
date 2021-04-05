---
title: 'チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)'
description: このチュートリアルでは、動的オブジェクトを作成および使用する方法について説明します。 カスタム動的オブジェクトと、'IronPython' ライブラリを使用するプロジェクトを作成します。
ms.date: 03/24/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.openlocfilehash: 3b342f23a2974affdcd7a1e91093aaef504afb63
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111024"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)

動的オブジェクトは、プロパティやメソッドなどのメンバーを、コンパイル時ではなく実行時に公開します。 これにより、静的な型や書式に一致しない構造体と連携するオブジェクトを作成することができます。 たとえば、動的オブジェクトを使用して HTML ドキュメント オブジェクト モデル (DOM) を参照することもできます。HTML DOM には、有効な HTML マークアップ要素と属性の任意の組み合わせを含めることができます。 各 HTML ドキュメントは一意であるため、特定の HTML ドキュメントのメンバーは実行時に決定されます。 HTML 要素の属性を参照するための一般的な方法は、属性の名前を要素の `GetProperty` メソッドに渡す方法です。 HTML 要素 `<div id="Div1">` の `id` 属性を参照するには、まず `<div>` 要素への参照を取得し、その後 `divElement.GetProperty("id")` を使用します。 動的オブジェクトを使用する場合は、`id` 属性を `divElement.id` として参照できます。

 動的オブジェクトを使用すると、IronPython や IronRuby などの動的言語にも簡単にアクセスできます。 動的オブジェクトを使用して、実行時に解釈される動的スクリプトを参照することもできます。

 動的オブジェクトを参照するには、遅延バインディングを使用します。 C# では、遅延バインディング オブジェクトの型は `dynamic` として指定します。 Visual Basic では、遅延バインディング オブジェクトの型は `Object` として指定します。 詳しくは、「[dynamic](../../language-reference/builtin-types/reference-types.md)」および「[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)」をご覧ください。

 カスタムの動的オブジェクトは、<xref:System.Dynamic?displayProperty=nameWithType> 名前空間内のクラスを使用して作成できます。 たとえば、<xref:System.Dynamic.ExpandoObject> を作成し、実行時にそのオブジェクトのメンバーを指定することもできます。 また、<xref:System.Dynamic.DynamicObject> クラスを継承する、独自の型を作成することもできます。 その後、<xref:System.Dynamic.DynamicObject> クラスのメンバーをオーバーライドして、実行時の動的機能を提供することができます。

 この記事には、次の 2 つの独立したチュートリアルがあります。

- テキスト ファイルの内容をオブジェクトのプロパティとして動的に公開する、カスタム オブジェクトを作成する。

- `IronPython` ライブラリを使用するプロジェクトを作成する。

これらのいずれかまたは両方を実行することができます。両方を実行する場合、順序は関係ありません。

## <a name="prerequisites"></a>前提条件

* **.NET デスクトップ開発** ワークロードがインストールされている [Visual Studio 2019 バージョン 16.9 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 このワークロードを選択すると、.NET 5.0 SDK が自動的にインストールされます。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

* 2 番目のチュートリアルでは、[IronPython](https://ironpython.net/) for .NET をインストールします。 最新バージョンを取得するには、[ダウンロード ページ](https://ironpython.net/download/)に移動します。

## <a name="create-a-custom-dynamic-object"></a>カスタム動的オブジェクトの作成

最初のチュートリアルでは、テキスト ファイルの内容を検索するカスタム動的オブジェクトを定義します。 動的プロパティにより、検索するテキストが指定されます。 たとえば、呼び出しコードで `dynamicFile.Sample` が指定された場合、動的クラスは "Sample" で始まるすべての行をファイルから取得し、それらを含んだ文字列のジェネリック リストを返します。 検索では、大文字と小文字を区別しません。 動的クラスでは、2 つの省略可能な引数もサポートされています。 最初の引数は、検索オプションの列挙値です。この引数では、動的クラスが行の先頭、行の末尾、または行内の任意の場所から一致を検索することを指定します。 2 番目の引数は、動的クラスが検索の前に各行から先頭と末尾の空白をトリミングすることを指定します。 たとえば、呼び出しコードで `dynamicFile.Sample(StringSearchOption.Contains)` と指定された場合、動的クラスは行内の任意の場所にある "Sample" を検索します。 呼び出しコードで `dynamicFile.Sample(StringSearchOption.StartsWith, false)` と指定された場合、動的クラスは、各行の先頭にある "Sample" を検索し、先頭と末尾のスペースは削除しません。 既定では、動的クラスは各行の先頭で一致を検索し、先頭と末尾のスペースを削除します。

### <a name="to-create-a-custom-dynamic-class"></a>カスタムの動的クラスを作成するには

1. Visual Studio を起動します。

1. **[新しいプロジェクトの作成]** を選択します。

1. **[新しいプロジェクトの作成]** ダイアログで、[C#] または [Visual Basic] を選択し、 **[コンソール アプリケーション]** を選択して、 **[次へ]** を選択します。

1. **[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** に「`DynamicSample`」と入力し、 **[次へ]** を選択します。

1. **[追加情報]** ダイアログで、 **[ターゲット フレームワーク]** に **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。

   新しいプロジェクトが作成されます。

1. **ソリューション エクスプローラー** で、DynamicSample プロジェクトを右リックし、 **[追加]**  >  **[クラス]** を選択します。 **[名前]** ボックスに「`ReadOnlyFile`」と入力し、 **[追加]** を選択します。

   ReadOnlyFile クラスを含んだ新しいファイルが追加されます。

1. *ReadOnlyFile.cs* または *ReadOnlyFile.vb* のファイルの先頭に、次のコードを追加して <xref:System.IO?displayProperty=nameWithType> および <xref:System.Dynamic?displayProperty=nameWithType> の名前空間をインポートします。

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]

1. カスタム動的オブジェクトでは、列挙型を使用して検索条件を決定します。 クラス ステートメントの前に、次の列挙定義を追加します。

    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]

1. 次のコード例に示すように、クラス ステートメントを更新して `DynamicObject` クラスを継承します。

    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

1. `ReadOnlyFile` クラスに次のコードを追加して、 ファイル パスのプライベート フィールドと、`ReadOnlyFile` クラスのコンス トラクターを定義します。

    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]

1. 次の `GetPropertyValue` メソッドを `ReadOnlyFile` クラスに追加します。 `GetPropertyValue` メソッドは検索条件を (入力として) 受け取り、テキスト ファイルから検索条件に一致する行を返します。 `ReadOnlyFile` クラスによって提供される動的メソッドは、`GetPropertyValue` メソッドを呼び出して、それぞれの結果を取得します。

    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]

1. `GetPropertyValue` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドをオーバーライドする次のコードを追加します。 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドは、動的クラスのメンバーが要求され、引数が指定されていない場合に呼び出されます。 `binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。

    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]

1. `TryGetMember` メソッドの後に、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドをオーバーライドする次のコードを追加します。 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドは、動的クラスのメンバーが引数を使用して要求された場合に呼び出されます。 `binder` 引数には、参照されているメンバーに関する情報が含まれます。`result` 引数は、指定したメンバーに対して返された結果を参照します。 `args` 引数には、メンバーに渡される引数の配列が含まれます。 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドはブール値を返します。要求されたメンバーが存在する場合には `true` を返し、その他の場合には `false` を返します。

    `TryInvokeMember` メソッドのカスタム バージョンは、1 つ目の引数として、前の手順で定義した `StringSearchOption` 列挙からの値を受け付けます。 `TryInvokeMember` メソッドは、2 つ目の引数としてブール値を受け付けます。 引数の一方または両方が有効な値であれば、それらが `GetPropertyValue` メソッドに渡され、結果が取得されます。

    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]

1. ファイルを保存して閉じます。

### <a name="to-create-a-sample-text-file"></a>サンプルのテキスト ファイルを作成するには

1. **ソリューション エクスプローラー** で、DynamicSample プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。 **[インストールされたテンプレート]** ペインで **[全般]** をクリックし、 **[テキスト ファイル]** テンプレートを選択します。 **[名前]** ボックスで、既定の名前である *TextFile1.txt* をそのままにし、 **[追加]** をクリックします。 新しいテキスト ファイルがプロジェクトに追加されます。

1. *TextFile1.txt* ファイルに次のテキストをコピーします。

    ```text
    List of customers and suppliers

    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)
    Customer: Preston, Chris
    Customer: Hines, Patrick
    Customer: Cameron, Maria
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan
    Customer: Koch, Paul
    ```

1. ファイルを保存して閉じます。

### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>カスタム動的オブジェクトを使用するサンプル アプリケーションを作成するには

1. **ソリューション エクスプローラー** で、Visual Basic をお使いの場合は *Program.vb* ファイルを、Visual C# をお使いの場合は *Program.cs* ファイルをダブルクリックします。

2. `Main` プロシージャに次のコードを追加して、*TextFile1.txt* ファイル用に `ReadOnlyFile` クラスのインスタンスを作成します。 このコードは、遅延バインディングを使用して動的メンバーを呼び出し、"Customer" という文字列を含んだテキスト行を取得します。

     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/Program.vb#8)]

3. ファイルを保存し、<kbd>Ctrl</kdb>+<kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。

## <a name="call-a-dynamic-language-library"></a>動的言語ライブラリの呼び出し

次のチュートリアルでは、動的言語 IronPython で記述されたライブラリにアクセスするプロジェクトを作成します。

### <a name="to-create-a-custom-dynamic-class"></a>カスタムの動的クラスを作成するには

1. Visual Studio で、 **[ファイル]**  >  **[新規]**  >  **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクトの作成]** ダイアログで、[C#] または [Visual Basic] を選択し、 **[コンソール アプリケーション]** を選択して、 **[次へ]** を選択します。

1. **[新しいプロジェクトの構成]** ダイアログで、 **[プロジェクト名]** に「`DynamicIronPythonSample`」と入力し、 **[次へ]** を選択します。

1. **[追加情報]** ダイアログで、 **[ターゲット フレームワーク]** に **[.NET 5.0 (Current)]** を選んでから、 **[作成]** を選択します。

   新しいプロジェクトが作成されます。

1. [IronPython](https://www.nuget.org/packages/IronPython) NuGet パッケージをインストールします。

1. Visual Basic をお使いの場合は、*Program.vb* ファイルを編集します。 Visual C# をお使いの場合は、*Program.cs* ファイルを編集します。

1. ファイルの先頭に次のコードを追加して、IronPython ライブラリと `System.Linq` 名前空間から `Microsoft.Scripting.Hosting` および `IronPython.Hosting` 名前空間をインポートします。

    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#1)]

1. Main メソッドで、IronPython ライブラリをホストする新しい `Microsoft.Scripting.Hosting.ScriptRuntime` オブジェクトを作成するための次のコードを追加します。 `ScriptRuntime` オブジェクトは、IronPython ライブラリ モジュール random.py を読み込みます。

     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#2)]

1. Random.py モジュールを読み込むコードの後に、整数の配列を作成する次のコードを追加します。 配列は random.py モジュールの `shuffle` メソッドに渡されます。このメソッドは、配列内の値をランダムに並べ替えします。

     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#3)]

1. ファイルを保存し、<kbd>Ctrl</kdb>+<kbd>F5</kbd> キーを押してアプリケーションをビルドし、実行します。

## <a name="see-also"></a>関連項目

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [dynamic 型の使用](./using-type-dynamic.md)
- [事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [動的なインターフェイスの実装 (Microsoft TechNet からダウンロードできる PDF)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
