---
title: 信頼性の規則 (コード分析)
description: コード分析の信頼性の規則について説明します。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a747dd4dcda351a1ddb0f3d069bb7bac895c32f8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591772"
---
# <a name="reliability-rules"></a>信頼性の規則

信頼性の規則は、メモリやスレッドの適切な使用など、ライブラリとアプリケーションの信頼性をサポートします。 次のような信頼性の規則があります。

|ルール|説明|
|----------|-----------------|
|[CA2000:スコープを失う前にオブジェクトを破棄](ca2000.md)|例外的なイベントが発生するとオブジェクトのファイナライザーを実行できないため、オブジェクトに対するすべての参照がスコープ外になる前に、オブジェクトを明示的に破棄する必要があります。|
|[CA2002:弱い ID を伴うオブジェクト上でロックしません](ca2002.md)|アプリケーション ドメインの境界を越えてオブジェクトに直接アクセスできる場合、そのオブジェクトの ID は不十分と表現されます。 スレッドで ID が不十分なオブジェクトをロックしようとすると、ブロックされることがあります。たとえば、異なるアプリケーション ドメインの別スレッドで、既に同じオブジェクトがロックされている場合です。|
|[CA2007:タスクを直接待機しないでください](ca2007.md)|非同期メソッドでは <xref:System.Threading.Tasks.Task> を直接[待機](../../../csharp/language-reference/operators/await.md)します。|
|[CA2008:TaskScheduler を渡さずにタスクを作成しない](ca2008.md)|タスクの作成または継続の操作で、<xref:System.Threading.Tasks.TaskScheduler> パラメーターを指定しないメソッド オーバーロードを使用しています。|
|[CA2009: ImmutableCollection 値で ToImmutableCollection を呼び出さないでください](ca2009.md)|`ToImmutable` メソッドが <xref:System.Collections.Immutable> 名前空間から変更できないコレクションで不必要に呼び出されました。|
|[CA2011: セッター内でプロパティを割り当てません](ca2011.md) | プロパティの [set アクセサー](../../../csharp/programming-guide/classes-and-structs/using-properties.md#the-set-accessor)内でプロパティに値が誤って割り当てられました。 |
|[CA2012: ValueTask を正しく使用する必要があります](ca2012.md) | メンバーの呼び出しから返される ValueTask は、直接待機される必要があります。  ValueTask を複数回使用しようとするか、完了が判明する前に結果に直接アクセスしようとすると、例外または破損が発生する可能性があります。  このような ValueTask を無視することは、機能的なバグを示していることが多く、パフォーマンスを低下させる可能性があります。 |
|[CA2013: 値の型と共に ReferenceEquals を使用しないでください](ca2013.md) | <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> を使用して値を比較するときに、objA と objB が値の型である場合、この 2 つは <xref:System.Object.ReferenceEquals%2A> メソッドに渡される前にボックス化されます。 つまり、objA と objB が同じ値の型のインスタンスを表している場合でも、<xref:System.Object.ReferenceEquals%2A> メソッドからは false が返されます。 |
|[CA2014: ループ内で stackalloc を使用しません](ca2014.md) | stackalloc によって割り当てられたスタック領域は、現在のメソッド呼び出しの終了時にのみ解放されます。  これをループ内で使用すると、スタックが無限に増加し、最終的にスタック オーバーフロー状態が発生する可能性があります。 |
|[CA2015: MemoryManager から派生した型にはファイナライザーを定義しません&lt;T&gt;](ca2015.md) | <xref:System.Buffers.MemoryManager%601> から派生した型にファイナライザーを追加すると、<xref:System.Span%601> によってまだ使用中のメモリが解放される可能性があります。 |
|[CA2016:CancellationToken パラメーターを 1 つのメソッドに転送する](ca2016.md) | `CancellationToken` パラメーターを 1 つを取るメソッドに転送して操作のキャンセル通知が適切に伝達されるようにするか、または `CancellationToken.None` を明示的に渡して意図的にトークンを伝達しないことを指定します。 |
