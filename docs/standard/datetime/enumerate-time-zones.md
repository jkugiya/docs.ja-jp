---
description: '詳細情報: コンピューター上に存在するタイム ゾーンを列挙する'
title: '方法: コンピューター上に存在するタイム ゾーンを列挙する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 98227d61ed81828f9c0614f622fed9a9667c6f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702679"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>方法: コンピューター上に存在するタイム ゾーンを列挙する

指定されたタイム ゾーンを正しく処理するには、そのタイム ゾーンに関する情報がシステムで使用できる必要があります。 Windows XP および Windows Vista オペレーティング システムでは、この情報はレジストリに格納されます。 しかし、世界中に存在するタイム ゾーンの合計数は大きいものの、レジストリにはそれらの一部に関する情報しか含まれません。 さらに、レジストリ自体は、内容が意図的に、および誤って変更される可能性がある動的な構造です。 その結果、アプリケーションは、特定のタイム ゾーンがシステムで定義され、使用できると常に想定することができません。 タイム ゾーン情報のアプリケーションを使用する多くのアプリケーションの最初の手順は、必要なタイム ゾーンがローカル システムで使用できるかどうかを判断する、またはタイム ゾーンの一覧をユーザーに提供して選択させることです。 これには、アプリケーションがローカル システムで定義されているタイム ゾーンを列挙する必要があります。

> [!NOTE]
> アプリケーションが、ローカル システムで定義されていない特定のタイム ゾーンの存在に依存している場合は、タイム ゾーンに関する情報をシリアル化および逆シリアル化することによってアプリケーションからその存在を確認できます。 その後、タイム ゾーンをリスト コントロールに追加して、アプリケーション ユーザーが選択できるようにできます。 詳細については、「[方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」および「[方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)」をご覧ください。

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>ローカル システムに存在するタイム ゾーンを列挙するには

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。 このメソッドから、<xref:System.TimeZoneInfo> オブジェクトのジェネリックの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションが返されます。 コレクション内のエントリは、その <xref:System.TimeZoneInfo.DisplayName%2A> プロパティによって並べ替えられます。 次に例を示します。

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. コレクション内の個々の <xref:System.TimeZoneInfo> オブジェクトを列挙するには `foreach` ループ (C# の場合) または `For Each`…`Next` ループ (Visual Basic の場合) を使用し、各オブジェクトに対して必要な処理を実行します。 たとえば、次のコードでは、手順 1 で返された <xref:System.TimeZoneInfo> オブジェクトの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションを列挙し、各タイム ゾーンの表示名をコンソールに一覧表示します。

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>ローカル システム上に存在するタイム ゾーンの一覧をユーザーに表示するには

1. <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> メソッドを呼び出します。 このメソッドから、<xref:System.TimeZoneInfo> オブジェクトのジェネリックの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションが返されます。

2. 手順 1 で返されたコレクションを、Windows フォームまたは ASP.NET のリスト コントロールの `DataSource` プロパティに割り当てます。

3. ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトを取得します。

Windows アプリケーションの場合の例を次に示します。

## <a name="example"></a>例

この例では、システムで定義されているタイム ゾーンをリスト ボックスに表示する Windows アプリケーションを開始します。 次いでこの例では、ユーザーによって選択されたタイム ゾーン オブジェクトの <xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値を含むダイアログ ボックスが表示されます。

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

ほとんどのリスト コントロール (<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> または <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> コントロールなど) では、オブジェクト変数のコレクションをコントロールの `DataSource` プロパティに割り当てることができます。ただし、そのコレクションが <xref:System.Collections.IEnumerable> インターフェイスを実装している必要があります。 (<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> ジェネリック クラスはその一例です)。コレクションの各オブジェクトを表示するため、コントロールでは、そのオブジェクトの `ToString` メソッドを呼び出して、オブジェクトを表現するために使用する文字列を抽出します。 <xref:System.TimeZoneInfo> オブジェクトの場合、`ToString` メソッドからは <xref:System.TimeZoneInfo> オブジェクトの表示名 (その <xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値) が返されます。

> [!NOTE]
> リスト コントロールではオブジェクトの `ToString` メソッドが呼び出されるため、オブジェクト <xref:System.TimeZoneInfo> のコレクションをコントロールに割り当てて、各オブジェクトのわかりやすい名前をコントロールに表示させ、ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトを取得することができます。 これにより、コレクション内の各オブジェクトについて文字列を抽出し、その文字列を別のコレクションに割り当てた後、そのコレクションをコントロールの `DataSource` プロパティに割り当てて、ユーザーが選択した文字列を取得し、その文字列を使用してそれが表しているオブジェクトを抽出する、という必要がなくなります。

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- 次の名前空間がインポートされていること。

  <xref:System> (C# コードの場合)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
- [方法: 埋め込みリソースにタイム ゾーンを保存する](save-time-zones-to-an-embedded-resource.md)
- [方法: 埋め込みリソースからタイム ゾーンを復元する](restore-time-zones-from-an-embedded-resource.md)
