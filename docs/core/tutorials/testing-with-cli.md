---
title: .NET CLI を使用したプロジェクトの整理とテスト
description: このチュートリアルでは、コマンド ラインから .NET プロジェクトを整理してテストする方法について説明します。
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: c668cff48a2418cc1bc34aef78ea26c863d9de6a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872679"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a>.NET CLI を使用したプロジェクトの整理とテスト

このチュートリアルでは、「[チュートリアル: Visual Studio Code を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-code.md)」に従って、簡単なコンソール アプリの作成より先に進んで、高度でよく構成されたアプリケーションの開発を行います。 フォルダーを使用してコードを整理する方法に続き、このチュートリアルでは [xUnit](https://xunit.net/) テスト フレームワークでコンソール アプリケーションを拡張する方法を示します。

## <a name="using-folders-to-organize-code"></a>フォルダーを使用してコードを整理する

コンソール アプリに新しいタイプを導入する場合、そのタイプを含むファイルをアプリに追加することができます。 たとえば、`AccountInformation` および `MonthlyReportRecords` タイプを含むファイルをプロジェクトに追加した場合、以下のように、プロジェクト ファイルの構造はフラットで移動しやすいものになります。

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

ただし、これはプロジェクトのサイズが比較的小さい場合にのみ適しています。 プロジェクトに 20 個のタイプを追加した場合はどうなるかというと、 プロジェクトのルート ディレクトリが乱雑になり、その多くのファイルの移動や維持が容易でなくなることは明らかです。

このようなプロジェクトを整理するには、新しいフォルダーを作成し、*Models* という名前を付けてタイプ ファイルを保持します。 以下のように、*Models* フォルダーにタイプ ファイルを配置します。

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

論理的にファイルをフォルダーにグループ化するプロジェクトでは、移動や維持が容易になります。 次のセクションでは、フォルダーと単体テストを使用してさらに複雑なサンプルを作成します。

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>NewTypes ペット サンプルを使用した整理とテスト

### <a name="prerequisites"></a>前提条件

* [.NET 5.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョン。

### <a name="building-the-sample"></a>サンプルのビルド

以下の手順では、[NewTypes ペット サンプル](https://github.com/dotnet/samples/tree/main/core/console-apps/NewTypesMsBuild)に従うことも、独自のファイルとフォルダーを作成することもできます。 タイプは、後でタイプをさらに追加することができるフォルダー構造に論理的に整理されます。また、テストも、後でテストをさらに追加できるフォルダーに論理的に配置されます。

サンプルには `Dog` と `Cat` という 2 つのタイプが含まれています。このサンプルでは `IPet` という共通インターフェイスを実装します。 `NewTypes` プロジェクトの目標は、*Pets* フォルダーにペット関連のタイプを整理することです。 別のタイプ セット (*WildAnimals* など) が後で追加された場合、それらは *Pets* フォルダーと同じ場所にある *NewTypes* フォルダーに配置されます。 *WildAnimals* フォルダーには、`Squirrel` や `Rabbit` タイプなど、ペットではない動物のタイプを含めることができます。 このようにタイプを追加すれば、プロジェクトはよく構成された状態に保たれます。

以下のようなファイル コンテンツのフォルダー構造を作成します。

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

次のコマンドを実行します。

```dotnetcli
dotnet run
```

次の出力を取得します。

```console
Woof!
Meow!
```

省略可能な演習:このプロジェクトを拡張し、`Bird` などの新しいペット タイプを追加することができます。 その場合、鳥の `TalkToOwner` メソッドで所有者に `Tweet!` を与えるようにします。 再度アプリを実行します。 出力には `Tweet!` が含まれます。

### <a name="testing-the-sample"></a>サンプルのテスト

これで、`NewTypes` プロジェクトの準備ができました。フォルダーにはペット関連のタイプが保持されており、プロジェクトは整理された状態です。 次は、テスト プロジェクトを作成し、[xUnit](https://xunit.net/) テスト フレームワークを使用してテストの作成を開始します。 単体テストでは、ペット タイプの動作を自動的にチェックして、正しく動作していることを確認することができます。

*src* フォルダーに移動して、*test* フォルダーを作成します。この中に *NewTypesTests* フォルダーが含まれます。 *NewTypesTests* フォルダーのコマンド プロンプトから、`dotnet new xunit` を実行します。 これによって、*NewTypesTests.csproj* と *UnitTest1.cs* という 2 つのファイルが生成されます。

現在、テスト プロジェクトでは `NewTypes` のタイプをテストすることはできません。`NewTypes` プロジェクトへのプロジェクト参照が必要になります。 プロジェクト参照を追加するには、以下の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

または、次のように、*NewTypesTests.csproj* ファイルに `<ItemGroup>` ノードを追加して、プロジェクト参照を手動で追加することもできます。

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* ファイルには以下のものが含まれます。

* `Microsoft.NET.Test.Sdk` (.NET テスト インフラストラクチャ) へのパッケージ参照
* `xunit` (xUnit テスト フレームワーク) へのパッケージ参照
* `xunit.runner.visualstudio` (テスト ランナー) へのパッケージ参照
* `NewTypes` (テスト対象コード) へのプロジェクト参照

*UnitTest1.cs* の名前を *PetTests.cs* に変更し、ファイル内のコードを以下の内容と置き換えます。

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

省略可能な演習:所有者に `Tweet!` を与える前述の `Bird` タイプを追加した場合は、テスト メソッドを *PetTests.cs* ファイル `BirdTalkToOwnerReturnsTweet` に追加し、`Bird` タイプに対して `TalkToOwner` メソッドが正しく動作することを確認します。

> [!NOTE]
> `expected` と `actual` の値は等しくなることが予想されますが、`Assert.NotEqual` チェックに対する初期アサーションでは、これらの値が *等しくない* と指定されています。 通常、テストのロジックを確認するために、最初は一度失敗するテストを作成します。 テストが失敗したことを確認したら、テストに合格できるようにするアサーションを調整します。

完全なプロジェクト構造を次に示します。

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

*test/NewTypesTests* ディレクトリから開始します。 [`dotnet test`](../tools/dotnet-test.md) コマンドを使用して、テストを実行します。 このコマンドは、プロジェクト ファイルで指定されたテスト ランナーを開始します。

予想どおり、テストは失敗し、コンソールには次の出力が表示されます。

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

テストのアサーションを `Assert.NotEqual` から `Assert.Equal` に変更します。

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

`dotnet test` を使用してテストを再実行し、次の出力を取得します。

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

テストに成功します。 ペット タイプのメソッドは、所有者との対話中に正しい値を返します。

これで、xUnit を使用してプロジェクトを整理し、テストする方法を習得できました。 次は、これらの方法を独自のプロジェクトに適用します。 *コーディングを楽しんでください。*
