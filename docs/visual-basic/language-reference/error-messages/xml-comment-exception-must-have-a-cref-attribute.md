---
description: "詳細情報: BC42319:XML コメントの例外には 'cref' 属性を指定しなければなりません"
title: XML コメントの例外には 'cref' 属性を指定しなければなりません
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: e602a2973d95f70d5ab532e6be319a9575d239a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701457"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="8276e-103">BC42319:XML コメントの例外には 'cref' 属性を指定しなければなりません</span><span class="sxs-lookup"><span data-stu-id="8276e-103">BC42319: XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="8276e-104">\<exception> タグは、メソッドによってスローされる可能性のある例外を文書化する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="8276e-104">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="8276e-105">必須の `cref` 属性は、ドキュメント生成機能によってチェックされるメンバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8276e-105">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="8276e-106">メンバーが存在する場合、そのメンバーはドキュメント ファイル内の正規要素名に変換されます。</span><span class="sxs-lookup"><span data-stu-id="8276e-106">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="8276e-107">**エラー ID:** BC42319</span><span class="sxs-lookup"><span data-stu-id="8276e-107">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8276e-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8276e-108">To correct this error</span></span>

<span data-ttu-id="8276e-109">次のように、例外に `cref` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="8276e-109">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="8276e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="8276e-110">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="8276e-111">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="8276e-111">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="8276e-112">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="8276e-112">XML Comment Tags</span></span>](../xmldoc/index.md)
