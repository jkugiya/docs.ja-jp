---
title: 標準例外型の使用
description: .NET での標準例外型について説明します。 SystemException、ApplicationException、ArgumentException、ComException などについて説明します。
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: ef420d47e6204aef5e3d9bc12ace31fbf5521ee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734362"
---
# <a name="using-standard-exception-types"></a>標準例外型の使用

このセクションでは、フレームワークによって提供される標準例外とその使用法の詳細について説明します。 このリストは完全なものではありません。 他のフレームワーク例外型の使用方法については、.NET Framework リファレンス ドキュメントを参照してください。

## <a name="exception-and-systemexception"></a>例外と SystemException

 ❌ <xref:System.Exception?displayProperty=nameWithType> または <xref:System.SystemException?displayProperty=nameWithType> をスローしないでください。

 ❌ 再スローする場合を除き、フレームワーク コード内で `System.Exception` または `System.SystemException` をキャッチしないでください。

 ❌ 最上位レベルの例外ハンドラー内の場合を除き、`System.Exception` または `System.SystemException` をキャッチすることは避けてください。

## <a name="applicationexception"></a>ApplicationException

 ❌ <xref:System.ApplicationException> をスローしたり、そこから派生させたりしないでください。

## <a name="invalidoperationexception"></a>InvalidOperationException

 ✔️ オブジェクトが不適切な状態にある場合は、<xref:System.InvalidOperationException> をスローしてください。

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、ArgumentNullException、ArgumentOutOfRangeException

 ✔️ 無効な引数がメンバーに渡された場合は、<xref:System.ArgumentException> またはそのサブタイプの 1 つをスローしてください。 最も多く派生した例外型を優先します (該当する場合)。

 ✔️ `ArgumentException` のサブクラスの 1 つをスローするときは、`ParamName` プロパティを設定してください。

 このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。 プロパティは、コンストラクターのオーバーロードの 1 つを使用して設定できることに注意してください。

 ✔️ プロパティ セッターの暗黙的な値パラメーターの名前には `value` を使用してください。

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException、AccessViolationException

 ❌ パブリックに呼び出し可能な API が <xref:System.NullReferenceException>、<xref:System.AccessViolationException>、または <xref:System.IndexOutOfRangeException> を明示的または暗黙的にスローすることを許可しないでください。 これらの例外は、実行エンジンによって予約およびスローされるもので、ほとんどの場合にバグを示します。

 これらの例外をスローしないように引数をチェックしてください。 これらの例外をスローすると、時間の経過と共に変化する可能性のあるメソッドの実装の詳細が公開されます。

## <a name="stackoverflowexception"></a>StackOverflowException

 ❌ <xref:System.StackOverflowException> を明示的にスローしないでください。 例外は、CLR によってのみ明示的にスローされる必要があります。

 ❌ `StackOverflowException` をキャッチしないでください。

 任意のスタック オーバーフローの有無に一貫性を持たせるマネージド コードを記述することはほぼ不可能です。 CLR のアンマネージド部分は、任意のスタック オーバーフローからバックアップするのではなく、プローブを使用してスタック オーバーフローを適切に定義された場所に移動することによって一貫性が保たれます。

## <a name="outofmemoryexception"></a>OutOfMemoryException

 ❌ <xref:System.OutOfMemoryException> を明示的にスローしないでください。 この例外は、CLR インフラストラクチャによってのみスローされます。

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException、ExecutionEngineException

 ❌ <xref:System.Runtime.InteropServices.COMException>、<xref:System.ExecutionEngineException>、<xref:System.Runtime.InteropServices.SEHException> を明示的にスローしないでください。 これらの例外は、CLR インフラストラクチャによってのみスローされます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [例外のデザインのガイドライン](exceptions.md)
