---
title: ASP.NET Web Forms と Blazor のアーキテクチャの比較
description: ASP.NET Web Forms と Blazor のアーキテクチャの比較について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: afb5d4025b81c2ddef782c462c94d32edc872a21
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509729"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>ASP.NET Web Forms と Blazor のアーキテクチャの比較

ASP.NET Web Forms と Blazor には多くの類似した概念がありますが、そのしくみには違いがあります。 この章では、ASP.NET Web Forms と Blazor の内部動作とアーキテクチャについて説明します。

## <a name="aspnet-web-forms"></a>ASP.NET Web Forms

ASP.NET Web Forms フレームワークは、ページ中心のアーキテクチャに基づいています。 アプリ内の場所に対する HTTP 要求はそれぞれ別個のページであり、ASP.NET ではそれを応答に使用します。 ページが要求されると、ブラウザーの内容は、要求されたページの結果に置き換えられます。

ページは、次のコンポーネントで構成されています。

- HTML マークアップ
- C# または Visual Basic コード
- ロジックおよびイベント処理機能を含む分離コード クラス
- コントロール

コントロールは、ページ上でプログラムによって配置および操作できる再利用可能な Web UI ユニットです。 ページは、マークアップ、コントロール、および何らかのコードを含む、 *.aspx* で終わるファイルで構成されます。 分離コード クラスは同じベース名のファイルに置かれ、使用するプログラミング言語に応じて拡張子が *.aspx.cs* または *.aspx.vb* になります。 興味深いことに、Web サーバーが *.aspx* ファイルの内容を解釈し、変更されるたびにコンパイルします。 この再コンパイルは、Web サーバーが既に実行されている場合でも発生します。

コントロールは、マークアップを使用して作成し、ユーザー コントロールとして提供できます。 ユーザー コントロールは `UserControl` クラスから派生し、ページと同様の構造を持ちます。 ユーザー コントロールのマークアップは *.ascx* ファイルに格納されます。 付随する分離コード クラスは、 *.ascx.cs* または *.ascx.vb* ファイルに置かれます。 コントロールは、`WebControl` または `CompositeControl` 基本クラスから継承することにより、完全にコードで作成することもできます。

ページには、広範なイベント ライフサイクルもあります。 各ページでは、ASP.NET ランタイムによって各要求のページのコードが実行されるときに発生する、初期化、ロード、プリレンダリング、およびアンロードの各イベントに対してイベントを発生させます。

通常、ページ上のコントロールは、コントロールが表示されていた同じページにポストバックされ、`ViewState` という名前の隠しフォーム フィールドからのペイロードを一緒に運びます。 `ViewState` フィールドには、コントロールがレンダリングされてページに表示された時点のコントロールの状態に関する情報が含まれています。これにより、ASP.NET ランタイムでは、サーバーに送信された内容を比較して変更を特定できます。

## Blazor

Blazor は、クライアント側の Web UI フレームワークであり、Angular や React などの JavaScript フロントエンド フレームワークに性質が似ています。 Blazor では、ユーザー操作が処理され、必要な UI の更新がレンダリングされます。 Blazor は、要求/応答モデルに基づいて *いません*。 ユーザー操作は、特定の HTTP 要求のコンテキストには含まれないイベントとして処理されます。

Blazor アプリは、HTML ページ上にレンダリングされる 1 つ以上のルート コンポーネントで構成されます。

![HTML 内の Blazor コンポーネント](./media/architecture-comparison/blazor-components-in-html.png)

コンポーネントをレンダリングする場所をユーザーが指定する方法と、ユーザー操作に対してコンポーネントを関連付ける方法は、[ホスティング モデル](hosting-models.md)に固有となります。

Blazor [コンポーネント](components.md)は、再利用可能な UI を表す .NET クラスです。 各コンポーネントは、自身の状態を保持し、自身のレンダリング ロジックを指定します。これには、他のコンポーネントのレンダリングを含めることができます。 コンポーネントは、コンポーネントの状態を更新するために、特定のユーザー操作のイベント ハンドラーを指定します。

コンポーネントでイベントが処理された後、Blazor によってコンポーネントがレンダリングされ、レンダリングされた出力の変更内容が追跡されます。 コンポーネントは、ドキュメント オブジェクト モデル (DOM) に直接はレンダリングされません。 代わりに、Blazor で変更を追跡できるように、`RenderTree` と呼ばれる DOM のメモリ内表現にレンダリングされます。 Blazor では、新しくレンダリングされた出力を前の出力と比較して UI の相違を計算してから、それを DOM に効率よく適用します。

![Blazor DOM の相互作用](./media/architecture-comparison/blazor-dom-interaction.png)

また、コンポーネントでは、その状態が通常の UI イベントの外部で変更された場合に、レンダリングが必要であることを手動で示すこともできます。 Blazor では、`SynchronizationContext` を使用して、1 つの論理スレッドを強制的に実行します。 コンポーネントの ライフサイクル メソッドと Blazor によって発生するイベント コールバックは、この `SynchronizationContext` で実行されます。

>[!div class="step-by-step"]
>[前へ](introduction.md)
>[次へ](hosting-models.md)
