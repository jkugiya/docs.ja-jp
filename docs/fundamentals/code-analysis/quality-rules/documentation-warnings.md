---
title: ドキュメント規則 (コード分析)
description: コード分析規則のドキュメント規則について
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591280"
---
# <a name="documentation-rules"></a>ドキュメント規則

ドキュメント規則では、外部から参照可能な API に [XML ドキュメント コメント](../../../csharp/codedoc.md)を正しく使用することによって、適切にドキュメント化されたライブラリの作成をサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
| - | - |
| [CA1200:プレフィックスで cref タグを使用しません](ca1200.md) | XML ドキュメント タグの [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 属性は "コード参照" を意味します。 タグの内部テキストが、型、メソッド、プロパティなど、コード要素であることを指定します。 `cref` タグとプレフィックスを一緒に使用すると、コンパイラで参照を検証できなくなるため、一緒に使用しないでください。 また、Visual Studio 統合開発環境 (IDE) でリファクタリング中にこれらのシンボル参照を見つけたり、更新したりすることもできなくなります。 |
