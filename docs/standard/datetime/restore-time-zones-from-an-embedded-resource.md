---
description: '詳細情報: 方法: 埋め込みリソースからタイム ゾーンを復元する'
title: '方法: 埋め込みリソースからタイム ゾーンを復元する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702484"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>方法: 埋め込みリソースからタイム ゾーンを復元する

このトピックでは、リソース ファイルに保存されているタイム ゾーンを復元する方法について説明します。 タイム ゾーンの保存に関する情報および手順については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」をご覧ください。

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化する方法

1. 取得するタイム ゾーンがカスタム タイム ゾーンでない場合は、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してインスタンス化してみてください。

2. 埋め込みリソース ファイルの完全修飾名と、リソース ファイルを含むアセンブリへの参照を渡すことによって、<xref:System.Resources.ResourceManager> オブジェクトをインスタンス化します。

   埋め込みリソース ファイルの完全修飾名を特定できない場合は、[Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用してアセンブリのマニフェストを確認します。 リソースを識別する `.mresource` エントリ。 この例では、リソースの完全修飾名は `SerializeTimeZoneData.SerializedTimeZones` です。

   リソース ファイルが、タイム ゾーンのインスタンス化コードを含むのと同じアセンブリに埋め込まれている場合は、`static` (Visual Basic の場合は `Shared`) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> メソッドを呼び出すことによって、それへの参照を取得できます。

3. <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドへの呼び出しが失敗する場合、またはカスタム タイム ゾーンをインスタンス化する場合は、<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> メソッドを呼び出して、シリアル化されたタイム ゾーンを含む文字列を取得します。

4. <xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを呼び出してタイム ゾーン データを逆シリアル化します。

## <a name="example"></a>例

次の例では、埋め込み .NET XML リソース ファイルに格納されている <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化します。

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

このコードでは、アプリケーションに必要な <xref:System.TimeZoneInfo> オブジェクトが存在することを確認するための例外処理を示します。 まず、<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> メソッドを使用してレジストリから <xref:System.TimeZoneInfo> オブジェクトを取得することによって、それのインスタンス化を試行します。 タイム ゾーンをインスタンス化できない場合、コードによって、埋め込みリソース ファイルからそれが取得されます。

カスタム タイム ゾーン (<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドを使用してインスタンス化されたタイム ゾーン) のデータはレジストリに格納されないため、コードで <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> が呼び出されて南極のパーマー基地のタイム ゾーンがインスタンス化されることはありません。 代わりに、埋め込みリソース ファイルがすぐに検索されて、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドが呼び出される前にタイム ゾーンのデータを含む文字列が取得されます。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- System.Windows.Forms.dll および System.Core.dll への参照がプロジェクトに追加されること。

- 次の名前空間がインポートされていること。

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [タイム ゾーンの概要](time-zone-overview.md)
- [方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)
