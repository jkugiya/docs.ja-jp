---
title: 破壊的変更:TreeNodeCollection.Item (Int32) から使用中のノードに対して ArgumentException がスローされる
description: 割り当て対象のノードが既に TreeView に割り当てられている場合、TreeNodeCollection.Item (Int32) から ArgumentException がスローされるようになったという、.NET 6 の破壊的変更について説明します。
ms.date: 01/19/2021
ms.openlocfilehash: 29727da2e4bc3d6ac89ed88819bf03d058603f77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255694"
---
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a>ノードが別のものに割り当てられている場合、TreeNodeCollection.Item により例外がスローされる

割り当て対象のノードが、別の <xref:System.Windows.Forms.TreeView> に、または別のインデックスでこの <xref:System.Windows.Forms.TreeView> に既にバインドされている場合、<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> から <xref:System.ArgumentException> がスローされます。

## <a name="change-description"></a>変更内容

以前の .NET バージョンでは、ツリー ノードが既に <xref:System.Windows.Forms.TreeView> にバインドされている場合でも、コレクションにツリー ノードを割り当てることができます。 これにより、重複するノードが発生する可能性があります。 .NET 6 以降、割り当て対象のノードが、別の <xref:System.Windows.Forms.TreeView> に、または別のインデックスでこの <xref:System.Windows.Forms.TreeView> に既にバインドされている場合、<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> から <xref:System.ArgumentException> がスローされます。

## <a name="reason-for-change"></a>変更理由

入力パラメーターの検証を、他の `TreeNodeCollection` API の動作と同じにします。

## <a name="version-introduced"></a>導入されたバージョン

.NET 6 Preview 1

## <a name="recommended-action"></a>推奨アクション

コレクションに割り当てる前に、必ず `TreeNode` のバインドを解除します。

## <a name="affected-apis"></a>影響を受ける API

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
