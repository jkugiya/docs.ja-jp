---
description: '詳細: 式'
title: 式-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: de16168585e2bbcbf8251c8e4b7c06784d72859d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742356"
---
# <a name="expressions"></a><span data-ttu-id="6cd39-103">式</span><span class="sxs-lookup"><span data-stu-id="6cd39-103">Expressions</span></span>

<span data-ttu-id="6cd39-104">Windows Workflow Foundation (WF) 式は、結果を返す任意のアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="6cd39-104">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="6cd39-105">すべての式アクティビティは、アクティビティの戻り値として <xref:System.Activities.Activity%601> という名前の <xref:System.Activities.OutArgument> プロパティを含む <xref:System.Activities.Activity%601.Result%2A> から間接的に派生します。</span><span class="sxs-lookup"><span data-stu-id="6cd39-105">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="6cd39-106">には、幅広い式アクティビティが用意されています。式アクティビティは、演算子アクティビティを介して 1 つのワークフロー変数へアクセスできる <xref:System.Activities.Expressions.VariableValue%601> や <xref:System.Activities.Expressions.VariableReference%601> などの単純なアクティビティから、結果を生成するために Visual Basic 言語一式へアクセスできる <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> や <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> などの複雑なアクティビティまでさまざまです。</span><span class="sxs-lookup"><span data-stu-id="6cd39-106">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="6cd39-107">追加の式アクティビティは、<xref:System.Activities.CodeActivity%601> または <xref:System.Activities.NativeActivity%601> から派生して作成できます。</span><span class="sxs-lookup"><span data-stu-id="6cd39-107">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="6cd39-108">式の使用</span><span class="sxs-lookup"><span data-stu-id="6cd39-108">Using Expressions</span></span>

 <span data-ttu-id="6cd39-109">ワークフロー デザイナーでは、Visual Basic プロジェクトのすべての式に <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> および <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601>、C# ワークフロー プロジェクトの式に <xref:Microsoft.CSharp.Activities.CSharpValue%601> および <xref:Microsoft.CSharp.Activities.CSharpReference%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="6cd39-109">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="6cd39-110">ワークフロープロジェクトでの C# 式のサポートは、.NET Framework 4.5 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="6cd39-110">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="6cd39-111">詳細については、「 [C# の式](csharp-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd39-111">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="6cd39-112">デザイナーによって生成されたワークフローは XAML に保存されます。XAML には、次の例のように、式が角かっこに囲まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="6cd39-112">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

```xml
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <Sequence.Variables>
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />
  </Sequence.Variables>
  <Assign>
    <Assign.To>
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>
    </Assign.To>
    <Assign.Value>
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>
    </Assign.Value>
  </Assign>
</Sequence>
```

 <span data-ttu-id="6cd39-113">コードでワークフローを定義すると、任意の式アクティビティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cd39-113">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="6cd39-114">次の例では、演算子アクティビティのコンポジションを使用して3つの数値を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6cd39-114">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new Add<int, int, int> {
                    Left = new Add<int, int, int> {
                        Left = new InArgument<int>(a),
                        Right = new InArgument<int>(b)
                    },
                    Right = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 <span data-ttu-id="6cd39-115">次の例に示すように、C# のラムダ式を使用すると、同じワークフローをさらにコンパクトに表現できます。</span><span class="sxs-lookup"><span data-stu-id="6cd39-115">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))
        }
    }
};
```

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="6cd39-116">カスタム式アクティビティによる使用可能な式の拡張</span><span class="sxs-lookup"><span data-stu-id="6cd39-116">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="6cd39-117">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] の式には、追加の式アクティビティを作成できる拡張性があります。</span><span class="sxs-lookup"><span data-stu-id="6cd39-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="6cd39-118">次のコードは、3 つの整数値の合計を返すアクティビティの例です。</span><span class="sxs-lookup"><span data-stu-id="6cd39-118">The following example shows an activity that returns a sum of three integer values.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Activities;

namespace ExpressionsDemo
{
    public sealed class AddThreeValues : CodeActivity<int>
    {
        public InArgument<int> Value1 { get; set; }
        public InArgument<int> Value2 { get; set; }
        public InArgument<int> Value3 { get; set; }

        protected override int Execute(CodeActivityContext context)
        {
            return Value1.Get(context) +
                   Value2.Get(context) +
                   Value3.Get(context);
        }
    }
}
```

 <span data-ttu-id="6cd39-119">この新しいアクティビティでは、次の例に示すように、3つの値を追加した前のワークフローを書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="6cd39-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

```csharp
Variable<int> a = new Variable<int>("a", 1);
Variable<int> b = new Variable<int>("b", 2);
Variable<int> c = new Variable<int>("c", 3);
Variable<int> r = new Variable<int>("r", 0);

Sequence w = new Sequence
{
    Variables = { a, b, c, r },
    Activities =
    {
        new Assign {
            To = new OutArgument<int>(r),
            Value = new InArgument<int> {
                Expression = new AddThreeValues() {
                    Value1 = new InArgument<int>(a),
                    Value2 = new InArgument<int>(b),
                    Value3 = new InArgument<int>(c)
                }
            }
        }
    }
};
```

 <span data-ttu-id="6cd39-120">コードで式を使用する方法の詳細については、「 [命令型コードを使用したワークフロー、アクティビティ、および式の作成](authoring-workflows-activities-and-expressions-using-imperative-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd39-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
