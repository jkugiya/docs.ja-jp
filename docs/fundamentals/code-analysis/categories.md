---
title: コード分析規則のカテゴリ
description: .NET コード分析規則のさまざまなカテゴリについて説明します。
ms.date: 02/05/2021
ms.topic: reference
helpviewer_keywords:
- code analysis, categories
ms.openlocfilehash: fdb4662f52a13906a2d9bcb3fd9a90860e394e72
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "100467330"
---
# <a name="rule-categories"></a>ルール カテゴリ

各コード分析規則は、規則のカテゴリに属しています。 たとえば、デザイン規則は .NET デザイン ガイドラインの順守をサポートし、セキュリティ規則はセキュリティの欠陥を防ぐのに役立ちます。 規則のカテゴリ全体に対して[重大度レベルを構成](configuration-options.md#scope)することができます。 カテゴリごとに[追加のオプションを構成](code-quality-rule-options.md#category-of-rules)することもできます。

次の表に、さまざまなコード分析規則のカテゴリと、各カテゴリの規則へのリンクを示します。

| カテゴリ | 説明 |
| - | - |
| [デザイン規則](quality-rules/design-warnings.md) | デザイン規則は、[.NET Framework デザイン ガイドライン](../../standard/design-guidelines/index.md)の順守をサポートします。 |
| [ドキュメント規則](quality-rules/documentation-warnings.md) | ドキュメント規則では、外部から参照可能な API に XML ドキュメント コメントを正しく使用することによって、適切にドキュメント化されたライブラリの作成をサポートします。 |
| [グローバリゼーション規則](quality-rules/globalization-warnings.md) | グローバリゼーション規則は、国際対応ライブラリおよびアプリケーションをサポートします。 |
| [移植性と相互運用性の規則](quality-rules/interoperability-warnings.md) | 移植性の規則は、異なるプラットフォーム間の移植性をサポートします。 相互運用性の規則は、COM クライアントとの対話をサポートします。 |
| [保守容易性の規則](quality-rules/maintainability-warnings.md) | 保守容易性の規則は、ライブラリとアプリケーションの保守をサポートします。 |
| [名前付け規則](quality-rules/naming-warnings.md) | 名前付け規則は、.NET デザイン ガイドラインの名前付け規則の順守をサポートします。 |
| [パフォーマンス ルール](quality-rules/performance-warnings.md) | パフォーマンス規則は、高パフォーマンスのライブラリとアプリケーションをサポートします。 |
| [規則の発行](quality-rules/publish-warnings.md) | 発行規則は、単一ファイル アプリケーションをサポートします。 |
| [信頼性の規則](quality-rules/reliability-warnings.md) | 信頼性の規則は、メモリやスレッドの適切な使用など、ライブラリとアプリケーションの信頼性をサポートします。 |
| [セキュリティ規則](quality-rules/security-warnings.md) | セキュリティ規則は、より安全なライブラリとアプリケーションをサポートします。 この規則によって、プログラムにセキュリティ上の欠陥が含まれるのを防ぐことができます。 |
| [スタイルの規則](style-rules/index.md) | スタイルの規則は、コードベースでの一貫性のあるコード スタイルをサポートします。 これらの規則は、"IDE" プレフィックスで始まります。 |
| [使い方の規則](quality-rules/usage-warnings.md) | 使い方の規則で、.NET の適切な使い方をサポートします。 |
