---
title: LINQ to XML の例をビルドする方法
description: このドキュメントの C# および Visual Basic コードでは、さまざまな名前空間からのクラスと型が使用されます。 コードをコンパイルして実行するには、名前空間にアクセスするための適切なディレクティブとステートメントを指定する必要があります。
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 94b2368e2c861f84d7db08fbbba57ef0f0da4d40
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411976"
---
# <a name="how-to-build-linq-to-xml-examples"></a>LINQ to XML の例をビルドする方法

このドキュメントに含まれているスニペットおよび例では、さまざまな名前空間からのクラスと型が使用されます。 C# コードをコンパイルするとき、適切な `using` ディレクティブを指定する必要があります。Visual Basic コードをコンパイルするとき、適切な `Imports` ステートメントを指定する必要があります。

## <a name="example"></a>例

次のコードには、C# のコード例をビルドおよび実行するために必要な `using` ディレクティブが含まれています。 すべての `using` ディレクティブがすべてのコード例で必要になるわけではありません。

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using System.Collections.Generic;
using System.Collections.Specialized;
using System.Text;
using System.Linq;
using System.Xml;
using System.Xml.Linq;
using System.Xml.Schema;
using System.Xml.XPath;
using System.Xml.Xsl;
using System.IO;
using System.Threading;
using System.Reflection;
using System.IO.Packaging;
```

次のコードには、Visual Basic のコード例をビルドおよび実行するために必要な `Imports` ステートメントが含まれています。 すべての `Imports` ステートメントがすべてのコード例で必要になるわけではありません。

```vb
Imports System.Diagnostics
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.Specialized
Imports System.Text
Imports System.Linq
Imports System.Xml
Imports System.Xml.Linq
Imports System.Xml.Schema
Imports System.Xml.XPath
Imports System.Xml.Xsl
Imports System.IO
Imports System.Threading
Imports System.Reflection
Imports System.IO.Packaging
```

## <a name="see-also"></a>関連項目

- [LINQ to XML の概要](linq-xml-overview.md)
