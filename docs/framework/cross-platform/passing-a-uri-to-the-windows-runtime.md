---
description: '詳細情報: Windows ランタイムへの URI の引き渡し'
title: Windows ランタイムへの URI の引き渡し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: 918f8ea71f4b23aeaf2a1295f2edd043a73a95ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402293"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Windows ランタイムへの URI の引き渡し

Windows ランタイムのメソッドは絶対 URI だけを受け取ります。 Windows ランタイム メソッドに相対 URI を渡すと、<xref:System.ArgumentException> 例外がスローされます。 これは、.NET Framework コードで Windows ランタイムを使用する場合、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> クラスは Intellisense では <xref:System.Uri?displayProperty=nameWithType> として示されるためです。 <xref:System.Uri?displayProperty=nameWithType> クラスでは相対 URI を使用できますが、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> クラスでは使用できません。 Windows ランタイム コンポーネントで公開するメソッドでも同様です。 URI を受け取るメソッドをコンポーネントで公開する場合、コードのシグネチャには <xref:System.Uri?displayProperty=nameWithType> が含まれます。 ただし、コンポーネントのユーザーに対しては、シグネチャに <xref:Windows.Foundation.Uri?displayProperty=nameWithType> が含まれます。 コンポーネントに渡す URI は、絶対 URI でなければなりません。  
  
このトピックでは、絶対 URI を検出する方法と、アプリ パッケージ内のリソースを参照するときに絶対 URI を作成する方法を説明します。  
  
## <a name="detecting-and-using-an-absolute-uri"></a>絶対 URI の検出と使用  

URI を Windows ランタイムに渡す前にそれが絶対 URI であることを確認するには、<xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> プロパティを使用します。 このプロパティを使用する方が、<xref:System.ArgumentException> 例外をキャッチして処理するより効率的です。  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>アプリ パッケージのリソースに対する絶対 URI の使用  

アプリのパッケージに含まれるリソースに対して URI を指定するには、`ms-appx` スキームまたは `ms-appx-web` スキームを使用して絶対 URI を作成します。  
  
次の例に、XAML とコードの両方を使用して、Pages という名前のフォルダーに含まれるリソースに、<xref:Windows.UI.Xaml.Controls.WebView> コントロールの <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> プロパティと <xref:Windows.UI.Xaml.Controls.Image> コントロールの <xref:Windows.UI.Xaml.Controls.Image.Source%2A> プロパティを設定する方法を示します。  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
これらのスキームの詳細については、Windows デベロッパー センターの「[URI スキーム](/windows/uwp/app-resources/uri-schemes)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](support-for-windows-store-apps-and-windows-runtime.md)
