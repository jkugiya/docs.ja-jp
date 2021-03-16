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
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="08bca-103">Windows ランタイムへの URI の引き渡し</span><span class="sxs-lookup"><span data-stu-id="08bca-103">Passing a URI to the Windows Runtime</span></span>

<span data-ttu-id="08bca-104">Windows ランタイムのメソッドは絶対 URI だけを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08bca-104">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="08bca-105">Windows ランタイム メソッドに相対 URI を渡すと、<xref:System.ArgumentException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="08bca-105">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="08bca-106">これは、.NET Framework コードで Windows ランタイムを使用する場合、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> クラスは Intellisense では <xref:System.Uri?displayProperty=nameWithType> として示されるためです。</span><span class="sxs-lookup"><span data-stu-id="08bca-106">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="08bca-107"><xref:System.Uri?displayProperty=nameWithType> クラスでは相対 URI を使用できますが、<xref:Windows.Foundation.Uri?displayProperty=nameWithType> クラスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="08bca-107">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="08bca-108">Windows ランタイム コンポーネントで公開するメソッドでも同様です。</span><span class="sxs-lookup"><span data-stu-id="08bca-108">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="08bca-109">URI を受け取るメソッドをコンポーネントで公開する場合、コードのシグネチャには <xref:System.Uri?displayProperty=nameWithType> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08bca-109">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08bca-110">ただし、コンポーネントのユーザーに対しては、シグネチャに <xref:Windows.Foundation.Uri?displayProperty=nameWithType> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08bca-110">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08bca-111">コンポーネントに渡す URI は、絶対 URI でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="08bca-111">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="08bca-112">このトピックでは、絶対 URI を検出する方法と、アプリ パッケージ内のリソースを参照するときに絶対 URI を作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="08bca-112">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="08bca-113">絶対 URI の検出と使用</span><span class="sxs-lookup"><span data-stu-id="08bca-113">Detecting and using an absolute URI</span></span>  

<span data-ttu-id="08bca-114">URI を Windows ランタイムに渡す前にそれが絶対 URI であることを確認するには、<xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="08bca-114">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="08bca-115">このプロパティを使用する方が、<xref:System.ArgumentException> 例外をキャッチして処理するより効率的です。</span><span class="sxs-lookup"><span data-stu-id="08bca-115">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="08bca-116">アプリ パッケージのリソースに対する絶対 URI の使用</span><span class="sxs-lookup"><span data-stu-id="08bca-116">Using an absolute URI for a resource in the app package</span></span>  

<span data-ttu-id="08bca-117">アプリのパッケージに含まれるリソースに対して URI を指定するには、`ms-appx` スキームまたは `ms-appx-web` スキームを使用して絶対 URI を作成します。</span><span class="sxs-lookup"><span data-stu-id="08bca-117">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="08bca-118">次の例に、XAML とコードの両方を使用して、Pages という名前のフォルダーに含まれるリソースに、<xref:Windows.UI.Xaml.Controls.WebView> コントロールの <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> プロパティと <xref:Windows.UI.Xaml.Controls.Image> コントロールの <xref:Windows.UI.Xaml.Controls.Image.Source%2A> プロパティを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="08bca-118">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="08bca-119">これらのスキームの詳細については、Windows デベロッパー センターの「[URI スキーム](/windows/uwp/app-resources/uri-schemes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08bca-119">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08bca-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="08bca-120">See also</span></span>

- [<span data-ttu-id="08bca-121">Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート</span><span class="sxs-lookup"><span data-stu-id="08bca-121">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
