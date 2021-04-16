---
title: 移植性と相互運用性の規則 (コード分析)
description: コード分析規則の移植性と相互運用性の規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591195"
---
# <a name="portability-and-interoperability-rules"></a>移植性と相互運用性の規則

移植性の規則は、異なるプラットフォーム間の移植性をサポートします。 相互運用性の規則は、COM クライアントとの対話をサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
| - | - |
| [CA1401: P/Invoke は参照可能になりません](ca1401.md) | パブリック型のパブリック メソッドまたはプロテクト メソッドに、System.Runtime.InteropServices.DllImportAttribute 属性があります (Visual Basic では Declare キーワードでも実装されます)。 このようなメソッドは公開しないでください。 |
| [CA1416:プラットフォームの互換性を検証する](ca1416.md) | プラットフォーム依存 API をコンポーネント上で使用すると、一部のプラットフォームでコードが動作しなくなります。 |
| [CA1417: P/Invokes の文字列パラメーターに `OutAttribute` を使用しません](ca1417.md) | 文字列がインターン処理された文字列で、文字列パラメーターが `OutAttribute` の値で渡された場合、ランタイムが不安定になる可能性があります。 |
