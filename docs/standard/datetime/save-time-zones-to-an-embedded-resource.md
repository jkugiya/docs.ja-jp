---
description: '詳細情報: 方法: 埋め込みリソースにタイム ゾーンを保存する'
title: '方法: 埋め込みリソースにタイム ゾーンを保存する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], saving
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
ms.openlocfilehash: 4f1455ffa790652d2dad605a0eb71fb81a05326d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702471"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>方法: 埋め込みリソースにタイム ゾーンを保存する

タイム ゾーンに対応するアプリケーションでは、多くの場合、特定のタイム ゾーンが存在する必要があります。 ただし、個々の <xref:System.TimeZoneInfo> オブジェクトの可用性は、ローカル システムのレジストリに格納されている情報によって異なるため、通常使用可能なタイム ゾーンも存在しない可能性があります。 また、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用してインスタンス化されたカスタム タイム ゾーンに関する情報は、他のタイム ゾーン情報と共にレジストリに格納されません。 これらのタイム ゾーンが必要なときに確実に使用できるようにするには、それらをシリアル化して保存し、後でそれらを逆シリアル化して復元します。

通常、<xref:System.TimeZoneInfo> オブジェクトのシリアル化は、タイム ゾーン対応アプリケーションとは別に行われます。 シリアル化された <xref:System.TimeZoneInfo> オブジェクトを保持するために使用されるデータ ストアに応じて、タイム ゾーン データは、セットアップまたはインストール ルーチンの一部として (たとえば、データがレジストリのアプリケーション キーに格納されている場合)、または最終的なアプリケーションをコンパイルする前に実行されるユーティリティ ルーチンの一部として (たとえば、シリアル化されたデータが .NET XML リソース (.resx) ファイルに格納されている場合)、シリアル化することができます。

アプリケーションと共にコンパイルされるリソース ファイルに加えて、他のいくつかのデータ ストアをタイム ゾーン情報に使用できます。 これらには、次のものが含まれます。

- レジストリ。 アプリケーションでは、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones のサブキーを使用するのではなく、独自のアプリケーション キーのサブキーを使用してカスタム タイム ゾーン データを格納する必要があることにご注意ください。

- 構成ファイル。

- その他のシステム ファイル。

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>タイム ゾーンを .resx ファイルにシリアル化して保存する方法

1. 既存のタイム ゾーンを取得するか、新しいタイム ゾーンを作成します。

   既存のタイム ゾーンを取得するには、「[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)」と「[TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)」をご覧ください。

   新しいタイム ゾーンを作成するには、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのいずれかのオーバーロードを呼び出します。 詳細については、「[方法: 調整規則のないタイム ゾーンを作成する](create-time-zones-without-adjustment-rules.md)」と「[方法: 調整規則のあるタイム ゾーンを作成する](create-time-zones-with-adjustment-rules.md)」をご覧ください。

2. <xref:System.TimeZoneInfo.ToSerializedString%2A> メソッドを呼び出して、タイム ゾーンのデータを含む文字列を作成します。

3. 名前を指定し、必要に応じて .resx ファイルへのパスを <xref:System.IO.StreamWriter> クラス コンストラクターに指定して、<xref:System.IO.StreamWriter> オブジェクトをインスタンス化します。

4. <xref:System.IO.StreamWriter> オブジェクトを <xref:System.Resources.ResXResourceWriter> クラス コンストラクターに渡すことによって、<xref:System.Resources.ResXResourceWriter> オブジェクトをインスタンス化します。

5. タイム ゾーンのシリアル化された文字列を <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> メソッドに渡します。

6. <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドを呼び出します。

7. <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出します。

8. <xref:System.IO.StreamWriter.Close%2A> メソッドを呼び出して、<xref:System.IO.StreamWriter> オブジェクトを閉じます。

9. 生成された .resx ファイルをアプリケーションの Visual Studio プロジェクトに追加します。

10. Visual Studio の **[プロパティ]** ウィンドウを使用して、.resx ファイルの **[ビルド アクション]** プロパティが **[埋め込みリソース]** に設定されていることを確認します。

## <a name="example"></a>例

次の例では、中部標準時を表す <xref:System.TimeZoneInfo> オブジェクトと、南極のパーマー基地の時刻を表す <xref:System.TimeZoneInfo> オブジェクトを、SerializedTimeZones.resx という名前の .NET XML リソース ファイルにシリアル化します。 通常、中部標準時はレジストリで定義されています。南極のパーマー基地はカスタム タイム ゾーンです。

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

この例では、コンパイル時にリソース ファイルで使用できるように <xref:System.TimeZoneInfo> オブジェクトをシリアル化します。

<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> メソッドは、完全なヘッダー情報を .NET XML リソース ファイルに追加するため、既存のファイルにリソースを追加するために使用することはできません。 この例では、SerializedTimeZones.resx ファイルを確認し、存在する場合は、2 つのシリアル化されたタイム ゾーン以外のすべてのリソースを汎用 <xref:System.Collections.Generic.Dictionary%602> オブジェクトに格納することで、この処理を行います。 その後、既存のファイルが削除され、既存のリソースが新しい SerializedTimeZones.resx ファイルに追加されます。 シリアル化されたタイム ゾーン データもこのファイルに追加されます。

リソースのキー (または **名前**) フィールドに、空白を埋め込むことはできません。 <xref:System.String.Replace%28System.String%2CSystem.String%29> メソッドは、リソース ファイルに割り当てられる前に、タイム ゾーン識別子内の埋め込まれた空白をすべて削除するために呼び出されます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加されること。

- 次の名前空間がインポートされていること。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [タイム ゾーンの概要](time-zone-overview.md)
- [方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)
