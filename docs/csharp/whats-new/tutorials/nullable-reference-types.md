---
title: null 許容参照型を使用して設計する
description: この高度なチュートリアルでは、null 許容参照型の概要について説明します。 参照値で null がいつ許容されるかに関する設計意図を表すことで、コンパイラで null が許容されるようにします。
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 01b05c6fa71c71546109cb25474b703458eb6e22
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104878925"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="8dc84-104">チュートリアル: null 許容参照型と null 非許容参照型を使用して設計意図をもっと明確に示す</span><span class="sxs-lookup"><span data-stu-id="8dc84-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="8dc84-105">C# 8.0 には [null 許容参照型](../../nullable-references.md)が導入されています。これは、null 許容値型が値型を補完するのと同じように、参照型を補完するものです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-105">C# 8.0 introduces [nullable reference types](../../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="8dc84-106">型に `?` を追加することで、変数が **null 許容参照型** であることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="8dc84-107">たとえば、`string?` は、null が許容される `string` を表します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="8dc84-108">これらの新しい型を使用して、一部の変数では *常に値を持つ必要があり*、他の変数では *値が欠落することも可能である* という設計意図をさらに明確に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="8dc84-109">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8dc84-110">null 許容参照型と null 非許容参照型を設計に組み込む。</span><span class="sxs-lookup"><span data-stu-id="8dc84-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="8dc84-111">コード全体で null 許容参照型をチェックできるようにする。</span><span class="sxs-lookup"><span data-stu-id="8dc84-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="8dc84-112">コンパイラでこれらの設計上の決定が適用されるコードを記述する。</span><span class="sxs-lookup"><span data-stu-id="8dc84-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="8dc84-113">自分の設計の中で null 許容参照機能を使用する。</span><span class="sxs-lookup"><span data-stu-id="8dc84-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8dc84-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8dc84-114">Prerequisites</span></span>

<span data-ttu-id="8dc84-115">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。C# 8.0 コンパイラも実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="8dc84-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="8dc84-116">C# 8.0 コンパイラは、[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) または [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet/3.0) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet/3.0).</span></span>

<span data-ttu-id="8dc84-117">このチュートリアルでは、.NET と、C# と Visual Studio または .NET Core CLI のいずれかに精通していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="8dc84-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="8dc84-118">null 許容参照型と null 非許容参照型を設計に組み込む</span><span class="sxs-lookup"><span data-stu-id="8dc84-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="8dc84-119">このチュートリアルでは、アンケートの実行をモデル化するライブラリを構築します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="8dc84-120">コードでは、null 許容参照型と null 非許容参照型の両方を使用して、現実世界の概念を表します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="8dc84-121">アンケートの質問は null することはできません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-121">The survey questions can never be null.</span></span> <span data-ttu-id="8dc84-122">回答者が質問に答えたくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="8dc84-123">この場合、応答は `null` になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="8dc84-124">このサンプルで記述するコードはそのような意図を表現し、コンパイラにその意図が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="8dc84-125">アプリケーションを作成し、null 許容参照型を有効にする</span><span class="sxs-lookup"><span data-stu-id="8dc84-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="8dc84-126">新しいコンソール アプリケーションを作成します。Visual Studio を使用するか、コマンド ラインで `dotnet new console` を使用します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="8dc84-127">アプリケーションに `NullableIntroduction` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="8dc84-128">アプリケーションを作成したら、プロジェクト全体が、有効な **null 許容注釈コンテキスト** でコンパイルされるように指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="8dc84-129">*.csproj* ファイルを開き、`Nullable` 要素を `PropertyGroup` 要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="8dc84-130">値を `enable`に設定します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-130">Set its value to `enable`.</span></span> <span data-ttu-id="8dc84-131">C# 8.0 プロジェクトであっても、**null 許容参照型** 機能を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="8dc84-132">これは、機能をオンにすると、既存の参照変数宣言が **null 非許容参照型** になるためです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="8dc84-133">その決定は既存のコードで適切な null チェックが行われていない場合に問題を発見するのに役立ちますが、元の設計意図が正確に反映されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="8dc84-134">アプリケーション用の型を設計する</span><span class="sxs-lookup"><span data-stu-id="8dc84-134">Design the types for the application</span></span>

<span data-ttu-id="8dc84-135">このアンケート アプリケーションでは、いくつかのクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="8dc84-136">質問の一覧をモデル化するクラス。</span><span class="sxs-lookup"><span data-stu-id="8dc84-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="8dc84-137">アンケートに応じてもらうために連絡した人物の一覧をモデル化するクラス。</span><span class="sxs-lookup"><span data-stu-id="8dc84-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="8dc84-138">アンケートに応じた人物から得た回答をモデル化するクラス。</span><span class="sxs-lookup"><span data-stu-id="8dc84-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="8dc84-139">これらの型では、null 許容参照型と null 非許容参照型の両方を利用して、必要なメンバーと省略可能なメンバーを表現します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="8dc84-140">null 許容参照型により、次の設計意図が明確に伝わります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="8dc84-141">アンケートの一部である質問を null にすることはできません。空の質問は意味がありません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="8dc84-142">回答者を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-142">The respondents can never be null.</span></span> <span data-ttu-id="8dc84-143">回答者が参加を辞退している場合でも、連絡した人物を追跡したいからです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="8dc84-144">質問に対する回答を null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-144">Any response to a question may be null.</span></span> <span data-ttu-id="8dc84-145">回答者は、一部の質問またはすべての質問の回答を拒否できます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="8dc84-146">これまで C# でプログラミングしている場合は、`null` 値を許容する参照型に慣れているため、null を許容しないインスタンスを宣言する機会がなかったかもしれません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="8dc84-147">質問のコレクションは null を許容しないものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="8dc84-148">回答者のコレクションは null を許容しないものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="8dc84-149">コードを記述していくにつれて、参照の既定値としての null 非許容参照型によって、<xref:System.NullReferenceException> を引き起こす可能性がある一般的なミスを回避できることを理解できるでしょう。</span><span class="sxs-lookup"><span data-stu-id="8dc84-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="8dc84-150">このチュートリアルから学ぶことの 1 つは、`null` にすることができる変数とできない変数を決定することです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="8dc84-151">この言語には、このような決定を表現するための構文が提供されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="8dc84-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="8dc84-152">今、それが実現しています。</span><span class="sxs-lookup"><span data-stu-id="8dc84-152">Now it does.</span></span>

<span data-ttu-id="8dc84-153">ビルドするアプリで、次の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="8dc84-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="8dc84-154">アンケートを作成し、そこに質問を追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="8dc84-155">アンケートの回答者の擬似乱数セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="8dc84-156">回答されたアンケートのサイズが目標数に達するまで、回答者に連絡します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="8dc84-157">アンケートの回答に関する重要な統計情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="8dc84-158">null 許容参照型と null 非許容参照型を含むアンケートを作成する</span><span class="sxs-lookup"><span data-stu-id="8dc84-158">Build the survey with nullable and non-nullable reference types</span></span>

<span data-ttu-id="8dc84-159">最初に記述するコードによって、アンケートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="8dc84-160">アンケートの質問とアンケートの実行をモデル化するクラスを記述します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="8dc84-161">アンケートには、回答の形式によって区別される 3 種類の質問があります:はい/いいえで回答するもの、番号で回答するもの、およびテキストで回答するもの。</span><span class="sxs-lookup"><span data-stu-id="8dc84-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="8dc84-162">`public SurveyQuestion` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="8dc84-163">コンパイラでは、有効な null 許容注釈コンテキスト内のコードについては、すべての参照型変数の宣言が **null 非許容** 参照型として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="8dc84-164">次のコードに示すように、質問のテキストと質問の種類のプロパティを追加することで、最初の警告を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="8dc84-165">`QuestionText` を初期化していないため、コンパイラによって、null を許容しないプロパティが初期化されていないことを示す警告が発行されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="8dc84-166">この設計では、質問のテキストを null 以外にする必要があるため、初期化するためのコンストラクターを追加します。`QuestionType` 値も同様にします。</span><span class="sxs-lookup"><span data-stu-id="8dc84-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="8dc84-167">完成したクラス定義は、次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="8dc84-168">コンストラクターを追加すると、警告が解除されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="8dc84-169">コンストラクターの引数も、null 非許容参照型であるため、コンパイラによる警告は発行されません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="8dc84-170">次に、`SurveyRun` という名前の `public` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="8dc84-171">次のコードに示すように、このクラスには、アンケートに質問を追加する `SurveyQuestion` オブジェクトとメソッドの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="8dc84-172">前と同じように、この一覧オブジェクトを null 以外の値に初期化する必要があります。そうしないとコンパイラによって警告が発行されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="8dc84-173">`AddQuestion` の 2 つ目のオーバーロードでは null のチェックは必要ないため、それが実行されることはありません。その変数は null 非許容であることが宣言されています。</span><span class="sxs-lookup"><span data-stu-id="8dc84-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="8dc84-174">その値は `null` になることはできません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-174">Its value can't be `null`.</span></span>

<span data-ttu-id="8dc84-175">お使いのエディターで *Program.cs* に切り替え、`Main` の内容を次のコード行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="8dc84-176">プロジェクト全体が、有効な null 許容注釈コンテキスト内にあるので、null 非許容参照型が必要なメソッドに `null` を渡すと、警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="8dc84-177">次の行を `Main` に追加して試してください。</span><span class="sxs-lookup"><span data-stu-id="8dc84-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="8dc84-178">回答者を作成し、アンケートに対する回答を取得する</span><span class="sxs-lookup"><span data-stu-id="8dc84-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="8dc84-179">次に、アンケートに対する回答を生成するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="8dc84-180">このプロセスには、いくつかの小さいタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="8dc84-181">回答者オブジェクトを生成するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="8dc84-182">これらは、アンケートへの入力を求められる人物を表します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="8dc84-183">回答者にアンケートを依頼し、回答を収集するか、回答者が回答しなかったことを示すデータを収集することをシミュレートするロジックを構築します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="8dc84-184">十分な数の回答者がアンケートに回答するまで、これを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="8dc84-185">アンケートの回答を表すクラスが必要なので、ここでそれを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="8dc84-186">null 許容のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8dc84-186">Enable nullable support.</span></span> <span data-ttu-id="8dc84-187">次のコードに示すように、`Id` プロパティとそれを初期化するコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="8dc84-188">次に、`static` メソッドを追加し、ランダム ID を生成することで新しい参加者を作成します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="8dc84-189">このクラスの主な役割は、アンケートの質問に対する参加者の回答を生成することです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="8dc84-190">この役割には、いくつかの手順があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="8dc84-191">アンケートへの参加を依頼します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-191">Ask for participation in the survey.</span></span> <span data-ttu-id="8dc84-192">回答者が同意しない場合は、応答の欠落 (つまり null) が返されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="8dc84-193">各質問を表示し、回答を記録します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-193">Ask each question and record the answer.</span></span> <span data-ttu-id="8dc84-194">回答も欠落する (つまり null になる) 可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="8dc84-195">`SurveyResponse` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="8dc84-196">アンケートの回答用のストレージは `Dictionary<int, string>?` であり、null が可能であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="8dc84-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="8dc84-197">新しい言語機能を使用して、コンパイラーと後日コードを読む人の両方に対して、設計意図が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="8dc84-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="8dc84-198">先に `null` 値のチェックを行わずに `surveyResponses` を逆参照した場合は、コンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="8dc84-199">`AnswerSurvey` メソッドで警告が表示されないのは、上記で `surveyResponses` 変数が null 以外の値に設定されたことをコンパイラが判断できるためです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="8dc84-200">欠落している回答に対して `null` を使用すると、null 許容参照型を処理するための重要なポイントが強調表示されます。目標は、プログラムからすべての `null` 値を削除することではありません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="8dc84-201">本当の目標は、記述しているコードで設計の意図が確実に表されるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="8dc84-202">欠落値は、コードでの表現に必要な概念です。</span><span class="sxs-lookup"><span data-stu-id="8dc84-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="8dc84-203">`null` 値は、これらの欠落値を表現する明確な方法です。</span><span class="sxs-lookup"><span data-stu-id="8dc84-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="8dc84-204">すべての `null` を削除しようとしても、`null` を使わずにそれらの欠落値を表すための他の何らかの方法を定義することになるだけです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="8dc84-205">次に、`SurveyRun` クラス内に `PerformSurvey` メソッドを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="8dc84-206">`SurveyRun` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="8dc84-207">ここでも、null を許容する `List<SurveyResponse>?` の選択によって、応答で null が可能であることが示されす。</span><span class="sxs-lookup"><span data-stu-id="8dc84-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="8dc84-208">これは、アンケートがまだ回答者に表示されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="8dc84-209">十分な数の同意が得られるまで回答者が追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8dc84-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="8dc84-210">アンケートを実行する最後の手順は、`Main` メソッドの最後にアンケートを実行する呼び出しを追加することです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="8dc84-211">アンケートの回答を調べる</span><span class="sxs-lookup"><span data-stu-id="8dc84-211">Examine survey responses</span></span>

<span data-ttu-id="8dc84-212">最後の手順は、アンケートの結果を表示することです。</span><span class="sxs-lookup"><span data-stu-id="8dc84-212">The last step is to display survey results.</span></span> <span data-ttu-id="8dc84-213">記述したクラスの多くにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="8dc84-214">このコードでは、null 許容参照型と null 非許容参照型を区別する値を示します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="8dc84-215">`SurveyResponse` クラスに次の 2 つの式形式メンバーを追加することから始めます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="8dc84-216">`surveyResponses` は null 許容参照型であるため、それを逆参照する前にチェックが必要です。</span><span class="sxs-lookup"><span data-stu-id="8dc84-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="8dc84-217">`Answer` メソッドからは null 非許容の文字列が返されます。そのため、null 合体演算子を使用して、不足している回答のケースをカバーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="8dc84-218">次に、次の 3 つの式形式メンバーを `SurveyRun` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="8dc84-219">`AllParticipants` メンバーでは、`respondents` 変数は null の場合があるが、戻り値を null にすることはできないことを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc84-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="8dc84-220">この式を `??` とその後ろの空のシーケンスを削除することで変更すると、コンパイラーによって、メソッドで `null` が返され、その戻り値のシグネチャで null 非許容型が返される可能性があることが警告されます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="8dc84-221">最後に、次のループを `Main` メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="8dc84-222">基になるインターフェースを非許容参照型を返すように設計しているため、このコードでは `null` のチェックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8dc84-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="8dc84-223">コードを取得する</span><span class="sxs-lookup"><span data-stu-id="8dc84-223">Get the code</span></span>

<span data-ttu-id="8dc84-224">[csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/main/csharp/NullableIntroduction) フォルダーの [samples](https://github.com/dotnet/samples) リポジトリから、完成したチュートリアルのコードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="8dc84-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/main/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="8dc84-225">null 許容参照型と null 非許容参照型の間で型宣言を変更することで試してください。</span><span class="sxs-lookup"><span data-stu-id="8dc84-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="8dc84-226">それによって生成される警告が変わることを確認して、`null` を間違って逆参照することがないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8dc84-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8dc84-227">次の手順</span><span class="sxs-lookup"><span data-stu-id="8dc84-227">Next steps</span></span>

<span data-ttu-id="8dc84-228">既存のアプリケーションを null 許容参照型を使用するように移行することについてさらに詳しく学習します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8dc84-229">Null 許容参照型を使用するようにアプリケーションをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="8dc84-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)

<span data-ttu-id="8dc84-230">Entity Framework を使用する場合に null 許容参照型を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dc84-230">Learn how to use nullable reference type when using Entity Framework:</span></span>
> [<span data-ttu-id="8dc84-231">Entity Framework Core の基礎: null 許容参照型の使用</span><span class="sxs-lookup"><span data-stu-id="8dc84-231">Entity Framework Core Fundamentals: Working with Nullable Reference Types</span></span>](/ef/core/miscellaneous/nullable-reference-types)
