---
description: '詳細情報: 方法:エンティティをシリアル化可能にする'
title: '方法: エンティティをシリアル化可能にする'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: cb2253d7933f3584543b4b030bc8b5aa3cc62921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785940"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="89835-103">方法: エンティティをシリアル化可能にする</span><span class="sxs-lookup"><span data-stu-id="89835-103">How to: Make Entities Serializable</span></span>

<span data-ttu-id="89835-104">コードを作成するときに、エンティティをシリアル化可能にできます。</span><span class="sxs-lookup"><span data-stu-id="89835-104">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="89835-105">エンティティ クラスは <xref:System.Runtime.Serialization.DataContractAttribute> 属性で装飾し、列は <xref:System.Runtime.Serialization.DataMemberAttribute> 属性で装飾します。</span><span class="sxs-lookup"><span data-stu-id="89835-105">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="89835-106">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーをこの目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="89835-106">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="89835-107">SQLMetal コマンド ライン ツールを使用する場合は、`unidirectional` 引数を指定して **/serialization** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="89835-107">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="89835-108">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89835-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89835-109">例</span><span class="sxs-lookup"><span data-stu-id="89835-109">Example</span></span>  

 <span data-ttu-id="89835-110">次の SQLMetal コマンド ラインでは、シリアル化可能なエンティティを持つファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="89835-110">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="89835-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="89835-111">See also</span></span>

- [<span data-ttu-id="89835-112">シリアル化</span><span class="sxs-lookup"><span data-stu-id="89835-112">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="89835-113">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="89835-113">Creating the Object Model</span></span>](creating-the-object-model.md)
