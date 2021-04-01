---
title: System.Text.Json でカスタム シリアライザーと逆シリアライザーを作成する方法
description: System.Text.Json 名前空間を使用して、JSON のカスタム シリアライザーと逆シリアライザーを作成する方法について説明します。
ms.date: 01/19/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 667c959584b553491caa672602b82be5649a79e4
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584834"
---
# <a name="how-to-write-custom-serializers-and-deserializers-with-systemtextjson"></a>System.Text.Json でカスタム シリアライザーと逆シリアライザーを作成する方法

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の、ハイパフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` または `ReadOnlySequence<byte>` から読み取られます。 `Utf8JsonReader` は低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために使用できます。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonReader` が使用されます。 `Utf8JsonReader` は Visual Basic コードから直接使用することはできません。 詳細については、「[Visual Basic のサポート](system-text-json-how-to.md#visual-basic-support)」をご覧ください。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、ハイパフォーマンスな方法です。 ライターは低レベルの型であり、カスタム シリアライザーを構築するために使用できます。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonWriter` が使用されます。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> では、`Utf8JsonReader` を使用して、読み取り専用のドキュメント オブジェクト モデル (DOM) を構築する機能が提供されます。 DOM では、JSON ペイロード内のデータへのランダム アクセスが提供されます。 ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> 型を使用してアクセスできます。 `JsonElement` 型では、配列とオブジェクト列挙子と共に、JSON テキストを一般的な .NET 型に変換する API が提供されます。 `JsonDocument` では <xref:System.Text.Json.JsonDocument.RootElement> プロパティが公開されます。

以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法を示します。

## <a name="use-jsondocument-for-access-to-data"></a>JsonDocument を使用してデータにアクセスする

次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して JSON 文字列内のデータにランダム アクセスする方法を示しています。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/JsonDocumentDataAccess.vb" id="AverageGrades1":::

上記のコードでは次の操作が行われます。

* 分析する JSON が `jsonString` という名前の文字列に含まれていると想定します。
* `Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。
* グレードのない学生には既定のグレード 70 を割り当てます。
* 反復するたびに `count` 変数をインクリメントして学生をカウントします。 別の方法として、次の例に示すように <xref:System.Text.Json.JsonElement.GetArrayLength%2A> を呼び出すこともできます。

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::
  :::code language="vb" source="snippets/system-text-json-how-to/vb/JsonDocumentDataAccess.vb" id="AverageGrades2":::

このコードで処理される JSON の例を次に示します。

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a>JsonDocument を使用して JSON を書き込む

次の例では、<xref:System.Text.Json.JsonDocument> から JSON を書き込む方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/JsonDocumentWriteJson.vb" id="Serialize":::

上記のコードでは次の操作が行われます。

* JSON ファイルを読み取り、データを `JsonDocument` に読み込み、書式設定された (整形された) JSON をファイルに書き込みます。
* <xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内でコメントは許可されるが無視されることを指定します。
* 完了したら、ライターに対して <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。 別の方法として、破棄されたときにライターを自動フラッシュすることもできます。

コード例によって処理される JSON 入力の例を次に示します。

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

その結果は、次のような整形された JSON 出力になります。

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter を使用する

<xref:System.Text.Json.Utf8JsonWriter> クラスを使用する方法を示す例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/Utf8WriterToStream.vb" id="Serialize":::

## <a name="use-utf8jsonreader"></a>Utf8JsonReader を使用する

<xref:System.Text.Json.Utf8JsonReader> クラスを使用する方法を示す例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/Utf8ReaderFromBytes.vb" id="Deserialize":::

上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを想定しています。

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader を使用してデータをフィルター処理する

次の例は、同期的にファイルを読み取り、値を検索する方法を示しています。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/Utf8ReaderFromFile.vb":::

この例の非同期バージョンについては、[.NET サンプル JSON プロジェクト](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)に関するページを参照してください。

上記のコードでは次の操作が行われます。

* JSON にオブジェクトの配列が含まれ、各オブジェクトに文字列型の "name" プロパティが含まれている可能性があると想定します。
* オブジェクトと "University" で終わる "name" プロパティ値をカウントします。
* ファイルが UTF-16 としてエンコードされ、UTF-8 にトランスコードされるものと想定します。 UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>` に直接読み取ることができます。

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  リーダーではテキストが想定されるため、ファイルに UTF-8 バイト オーダー マーク (BOM) が含まれている場合は、バイトを `Utf8JsonReader` に渡す前にそれを削除します。 そうしないと、BOM は無効な JSON と見なされ、リーダーによって例外がスローされます。

上記のコードで読み取ることができる JSON のサンプルを次に示します。 結果として生成される概要メッセージは、"2 out of 4 have names that end with 'University'" です。

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Utf8JsonReader を使用してストリームから読み取る

大きなファイル (ギガバイト以上のサイズなど) を読み取る場合、一度にファイル全体をメモリに読み込む必要を回避することができます。 このシナリオでは、<xref:System.IO.FileStream> を使用できます。

`Utf8JsonReader` を使用してストリームから読み取る場合、次の規則が適用されます。

* 部分的な JSON ペイロードが格納されるバッファーは、リーダーが処理を進めることができるように、少なくともその中で最大の JSON トークンと同じ大きさにする必要があります。
* バッファーは、少なくとも JSON 内の空白の最大シーケンスと同じ大きさである必要があります。
* リーダーでは、JSON ペイロード内の次の <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> が完全に読み取られるまで、読み取られたデータが追跡されません。 そのため、バッファー内にバイトが残っている場合は、再びリーダーに渡す必要があります。 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> を使用して、残っているバイト数を確認できます。

次のコードは、ストリームから読み取る方法を示しています。 この例は、<xref:System.IO.MemoryStream> を示しています。 同様のコードが <xref:System.IO.FileStream> で機能しますが、開始時に UTF-8 BOM が `FileStream` に含まれている場合を除きます。 その場合は、残りのバイトを `Utf8JsonReader` に渡す前に、バッファーからこれらの 3 バイトを取り除く必要があります。 そうしないと、BOM は JSON の有効な部分と見なされないため、リーダーによって例外がスローされます。

このサンプル コードでは、4 KB のバッファーから開始し、サイズが完全な JSON トークンに対応するのに十分な大きさではないことが判明するたびにバッファー サイズを 2 倍にします。これは、リーダーが JSON ペイロードの処理を進めるために必要です。 スニペットに用意されている JSON サンプルでは、非常に小さい初期バッファー サイズ (たとえば、10 バイト) を設定した場合にのみ、バッファー サイズが増加します。 初期バッファー サイズを 10 に設定すると、`Console.WriteLine` ステートメントによって、バッファー サイズの増加の原因と影響が示されます。 4 KB の初期バッファー サイズで、サンプルの JSON 全体が各 `Console.WriteLine` によって表示され、バッファー サイズを増やす必要はありません。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/Utf8ReaderPartialRead.vb":::

前の例では、バッファーを拡大できる最大の大きさを無制限に設定しています。 トークン サイズが大きすぎる場合、コードは <xref:System.OutOfMemoryException> 例外で失敗する可能性があります。 これは、JSON にサイズが約 1 GB 以上のトークンが含まれている場合に発生する可能性があります。1 GB のサイズを 2 倍にすると、サイズが大きすぎて `int32` バッファーに入り切らないためです。

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [文字エンコードをカスタマイズする方法](system-text-json-character-encoding.md)
* [JSON シリアル化のためのカスタム コンバーターを作成する方法](system-text-json-converters-how-to.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
