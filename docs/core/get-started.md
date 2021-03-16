---
title: .NET の使用を開始する
description: Hello World .NET アプリを作成します。
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.openlocfilehash: f196f5cfe914fe7ecddec61d2abf618c21968bbd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105155"
---
# <a name="get-started-with-net"></a>.NET を使って作業を開始する

この記事では、"Hello World!" .NET アプリを作成して実行する方法について説明します。 .NET アプリ。

.NET についてよくわからない場合は、[.NET の概要](introduction.md)のページからお読みください。

## <a name="create-an-application"></a>アプリケーションの作成

まず、ご利用のコンピューターで [.NET SDK](https://dotnet.microsoft.com/download/dotnet) をダウンロードしてインストールします。

次に、**PowerShell**、**コマンド プロンプト**、**bash** などのターミナルを開きます。 次の `dotnet` コマンドを入力し、C# アプリケーションを作成して実行します。

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

次の出力が表示されます。

```output
Hello World!
```

お疲れさまでした。 シンプルな .NET アプリケーションを作成しました。

## <a name="next-steps"></a>次のステップ

[ステップバイステップのチュートリアル](../standard/get-started.md)に従って、または YouTube で [.NET 101 の動画](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80)を視聴して、.NET アプリケーションの開発を開始します。
