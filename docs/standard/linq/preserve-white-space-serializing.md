---
title: シリアル化時に空白を維持する - LINQ to XML
description: XML ツリーをシリアル化するとき、さまざまな方法で空白を制御できます。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411984"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a>シリアル化時に空白を維持する (LINQ to XML)

この記事では、XML ツリーをシリアル化するときに空白を制御する方法について説明します。

一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが LINQ to XML の既定の動作です。

もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 LINQ to XML でこれを行うには、XML を読み込む際または解析する場合に空白を維持し、XML をシリアル化するときに書式設定を無効にします。

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ツリーをシリアル化するメソッドの空白に関する動作

<xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。 XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。 `ToString` メソッドは、文字列にシリアル化します。

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。 この場合、XML ツリー内の意味のない空白はすべて破棄されます。

メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。 この場合、XML ツリー内の空白はすべて維持されます。
