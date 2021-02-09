---
description: "詳細情報: BC40029: '<classname>' は継承元のインターフェイス '<interfacename>' が CLS に準拠していないため、CLS に準拠していません"
title: "'<classname>' は継承元のインターフェイス '<interfacename>' が CLS に準拠していないため、CLS に準拠していません。"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 28264dd602bd20a6b33bebd965982ca12d402d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796770"
---
# <a name="bc40029-classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="9a49e-103">BC40029: '\<classname>' は継承元のインターフェイス '\<interfacename>' が CLS に準拠していないため、CLS に準拠していません</span><span class="sxs-lookup"><span data-stu-id="9a49e-103">BC40029: '\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>

<span data-ttu-id="9a49e-104">クラスまたはインターフェイスが `<CLSCompliant(True)>` としてマークされていますが、これらの派生元の型、またはこれらが実装している型が `<CLSCompliant(False)>` としてマークされているか、マークされていません。</span><span class="sxs-lookup"><span data-stu-id="9a49e-104">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>

 <span data-ttu-id="9a49e-105">クラスまたはインターフェイスを[言語への非依存性および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、その継承階層全体を準拠させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a49e-105">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="9a49e-106">つまり、直接的または間接的に継承する型をすべて CLS に準拠させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a49e-106">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="9a49e-107">同様に、クラスが 1 つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a49e-107">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>

 <span data-ttu-id="9a49e-108">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。</span><span class="sxs-lookup"><span data-stu-id="9a49e-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="9a49e-109">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a49e-109">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="9a49e-110">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9a49e-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="9a49e-111">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="9a49e-111">By default, this message is a warning.</span></span> <span data-ttu-id="9a49e-112">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a49e-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="9a49e-113">**エラー ID:** BC40029</span><span class="sxs-lookup"><span data-stu-id="9a49e-113">**Error ID:** BC40029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9a49e-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9a49e-114">To correct this error</span></span>

- <span data-ttu-id="9a49e-115">CLS 準拠にする必要がある場合は、この型を別の継承階層または実装スキームの中で定義します。</span><span class="sxs-lookup"><span data-stu-id="9a49e-115">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>

- <span data-ttu-id="9a49e-116">この型を現在の継承階層または実装スキームに残しておく必要がある場合は、 <xref:System.CLSCompliantAttribute> を定義から削除するか、 `<CLSCompliant(False)>`としてマークします。</span><span class="sxs-lookup"><span data-stu-id="9a49e-116">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>
