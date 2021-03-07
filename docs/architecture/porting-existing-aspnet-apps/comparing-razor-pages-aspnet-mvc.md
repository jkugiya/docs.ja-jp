---
title: Razor Pages と ASP.NET MVC の比較
description: Razor Pages は、ページベースのアプリ用の従来の MVC ビューよりも、役割をより適切に整理する方法を提供します。 このセクションの従来の ASP.NET MVC アプローチと比較する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c188e7336e129fa710002081f1bef1f635cbe1fd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401399"
---
# <a name="compare-razor-pages-to-aspnet-mvc"></a>Razor Pages と ASP.NET MVC の比較

Razor Pages は、ASP.NET Core でページベースまたはフォームベースのアプリを作成する場合に推奨される方法です。 この [ドキュメント](/aspnet/core/razor-pages/)からは、"Razor Pages を使用すると、コントローラーとビューを使用するよりも簡単かつ生産性を高めることができます。 ASP.NET MVC アプリでビューを多用する場合は、アクションとビューから Razor Pages に移行することを検討してください。

厳密に型指定された一般的なビューベースの MVC アプリは、1つまたは複数のアクションを含むコントローラーを使用します。 コントローラーはドメインまたはデータモデルと対話し、ビューモデルクラスのインスタンスを作成します。 その後、このビューモデルクラスは、そのアクションに関連付けられたビューに渡されます。 このアプローチを MVC アプリの既定のフォルダー構造と組み合わせて使用することで、新しいページをアプリに追加するには、1つのフォルダー内のコントローラー、別のフォルダー内の入れ子になったサブフォルダー内のビュー、および他のフォルダー内のビューモデルを変更する必要があります。

Razor Pages、1つのクラスでアクション (現在は *ハンドラー*) とビューモデル ( *PageModel* と呼ばれます) をグループ化し、このクラスをビュー (Razor ページと呼ばれます) にリンクします。 すべての Razor Pages は、ASP.NET Core プロジェクトのルートにある *Pages* フォルダーに入ります。 Razor Pages、このフォルダー内の名前と場所に基づいてルーティング規則を使用します。 ハンドラーは、アクションメソッドとまったく同じように動作しますが、名前で処理される HTTP 動詞があります (たとえば、 `OnGet` )。 また、必ずしもを返す必要はありません。既定では、関連付けられているページが返されると想定されているためです。 これは、アプリの特定の部分を追加または変更するために必要なすべてのファイルを簡単に検索して使用できるようにすると同時に、Razor Pages とそのハンドラーを小さくして焦点を合わせたままにする傾向があります。

ASP.NET MVC から ASP.NET Core への移行の一環として、コントローラーとビューを ASP.NET Core コントローラーとビュー、または Razor Pages に移行するかどうかをチームで検討する必要があります。 前者では、ほとんどの場合、全体的な作業は少ししか必要ありませんが、従来のビューベースのファイル組織で Razor Pages の利点を活用することはできません。

## <a name="references"></a>関連項目

- [ASP.NET Core での Razor ページの概要](/aspnet/core/razor-pages/)
- [Razor Pages を使用した簡単な ASP.NET Core アプリ](/archive/msdn-magazine/2017/september/asp-net-core-simpler-asp-net-mvc-apps-with-razor-pages)

>[!div class="step-by-step"]
>[前へ](routing-differences.md)
>[次へ](webapi-differences.md)
