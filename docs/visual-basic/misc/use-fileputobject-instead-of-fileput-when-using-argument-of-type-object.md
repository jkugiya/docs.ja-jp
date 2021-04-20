---
description: "詳細情報: 型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください"
title: 型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460099"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。

`FilePut` メソッドには、型 `Object`の引数が含まれています。 あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `FilePut` を `FilePutObject` で置き換え  
  
- `Object` 引数をより具体的な種類にキャストします。  
  
- `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
