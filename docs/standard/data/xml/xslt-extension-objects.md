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
# <a name="xslt-extension-objects"></a>XSLT 拡張オブジェクト

拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。 拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。  
  
 埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。  
  
- クラスをより効果的にカプセル化および再利用できます。  
  
- スタイル シートを小さくすることができ、管理が簡単になります。  
  
 XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。 その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。 詳細については、「[コード アクセス セキュリティ](../../../framework/misc/code-access-security.md)」および「[名前付きアクセス許可セット](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))」を参照してください。  
  
 拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。  
  
 現在、`params` キーワードを使用して定義されるメソッド (不特定数のパラメーターを渡すことができる) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。 `params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。 詳細については、[params](../../../csharp/language-reference/keywords/params.md) に関するページを参照してください。  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT 拡張オブジェクトを使用するために必要な処理  
  
1. <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。  
  
2. スタイル シートから拡張オブジェクトを呼び出します。  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。  
  
## <a name="see-also"></a>関連項目

- [XSLT 変換](xslt-transformations.md)
- [XSLT のセキュリティに関する考慮事項](xslt-security-considerations.md)
