---
description: '詳細情報: XSLT 拡張オブジェクト'
title: XSLT 拡張オブジェクト
ms.date: 03/30/2017
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 5fc4ee8b3828219bc298a3ffc4c81bc342e2f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782534"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="64f90-103">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="64f90-103">XSLT Extension Objects</span></span>

<span data-ttu-id="64f90-104">拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="64f90-104">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="64f90-105">拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。</span><span class="sxs-lookup"><span data-stu-id="64f90-105">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="64f90-106">埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="64f90-106">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="64f90-107">クラスをより効果的にカプセル化および再利用できます。</span><span class="sxs-lookup"><span data-stu-id="64f90-107">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="64f90-108">スタイル シートを小さくすることができ、管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="64f90-108">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="64f90-109">XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="64f90-109">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="64f90-110">その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="64f90-110">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64f90-111"><xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。</span><span class="sxs-lookup"><span data-stu-id="64f90-111">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="64f90-112">詳細については、「[コード アクセス セキュリティ](../../../framework/misc/code-access-security.md)」および「[名前付きアクセス許可セット](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f90-112">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="64f90-113">拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="64f90-113">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="64f90-114">現在、`params` キーワードを使用して定義されるメソッド (不特定数のパラメーターを渡すことができる) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="64f90-114">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="64f90-115">`params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="64f90-115">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="64f90-116">詳細については、[params](../../../csharp/language-reference/keywords/params.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="64f90-116">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="64f90-117">XSLT 拡張オブジェクトを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="64f90-117">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="64f90-118"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="64f90-118">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="64f90-119">スタイル シートから拡張オブジェクトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64f90-119">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="64f90-120"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="64f90-120">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f90-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="64f90-121">See also</span></span>

- [<span data-ttu-id="64f90-122">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="64f90-122">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="64f90-123">XSLT のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="64f90-123">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
