---
title: 破壊的変更:null 許容参照型の注釈の変更
description: .NET 6.0 のコア .NET ライブラリで、null 許容参照型の注釈が一部変更されたことによる破壊的変更について説明します。
ms.date: 02/11/2021
ms.openlocfilehash: a0133ce49ba33d0e835b718f3f2b19180526c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488225"
---
# <a name="changes-to-nullable-reference-type-annotations"></a><span data-ttu-id="26140-103">null 許容参照型の注釈の変更</span><span class="sxs-lookup"><span data-stu-id="26140-103">Changes to nullable reference type annotations</span></span>

<span data-ttu-id="26140-104">.NET 6.0 の .NET ライブラリの null 許容参照型の注釈が一部変更されました。</span><span class="sxs-lookup"><span data-stu-id="26140-104">In .NET 6.0, some nullability annotations in the .NET libraries have changed.</span></span>

## <a name="change-description"></a><span data-ttu-id="26140-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="26140-105">Change description</span></span>

<span data-ttu-id="26140-106">以前のバージョンの .NET では、一部の null 許容照型の注釈が正しくなく、ビルド警告がない、または正しくありませんでした。</span><span class="sxs-lookup"><span data-stu-id="26140-106">In previous .NET versions, some nullable reference type annotations are incorrect, and build warnings are either absent or incorrect.</span></span> <span data-ttu-id="26140-107">.NET 6.0 以降では、以前適用されていた一部の注釈が更新されています。</span><span class="sxs-lookup"><span data-stu-id="26140-107">Starting in .NET 6.0, some annotations that were previously applied have been updated.</span></span> <span data-ttu-id="26140-108">影響を受ける API は、新しいビルド警告を生成し、正しくないビルド警告を生成しません。</span><span class="sxs-lookup"><span data-stu-id="26140-108">New build warnings will be produced and incorrect build warnings will no longer be produced for the affected APIs.</span></span>

<span data-ttu-id="26140-109">これらの変更の一部は、ビルド時に新しい警告を発する可能性があるため、"*破壊的*" と見なされています。</span><span class="sxs-lookup"><span data-stu-id="26140-109">Some of these changes are considered to be *breaking* because they can lead to new build-time warnings.</span></span> <span data-ttu-id="26140-110">.NET 6.0 に移行するときは、これらの API を参照するコードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26140-110">When you migrate to .NET 6.0, code that references these APIs will need to be updated.</span></span>

<span data-ttu-id="26140-111">このページでは、破壊的と見なされないその他の変更についても説明しています。</span><span class="sxs-lookup"><span data-stu-id="26140-111">Other changes that aren't considered to be breaking are also documented on this page.</span></span> <span data-ttu-id="26140-112">更新された API を参照するコードには、不要になった演算子やプラグマを削除できることによってメリットがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="26140-112">Any code that references the updated APIs may benefit from removing operators or pragmas that are no longer unnecessary.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="26140-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="26140-113">Version introduced</span></span>

<span data-ttu-id="26140-114">6.0</span><span class="sxs-lookup"><span data-stu-id="26140-114">6.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="26140-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="26140-115">Reason for change</span></span>

<span data-ttu-id="26140-116">.NET Core 3.0 以降、null 値を許容する注釈が .NET ライブラリに適用されました。</span><span class="sxs-lookup"><span data-stu-id="26140-116">Starting in .NET Core 3.0, nullability annotations were applied to the .NET libraries.</span></span> <span data-ttu-id="26140-117">この取り組みでは当初から、これらの注釈に誤りがあることが予想されていました。</span><span class="sxs-lookup"><span data-stu-id="26140-117">From the outset of the effort, mistakes in these annotations were anticipated.</span></span> <span data-ttu-id="26140-118">フィードバックとさらなるテストから、影響を受ける API での null 値が許容される注釈は不正確であると判断されました。</span><span class="sxs-lookup"><span data-stu-id="26140-118">Through feedback and further testing, the nullable annotations for the affected APIs were determined to be inaccurate.</span></span> <span data-ttu-id="26140-119">更新された注釈では、それらの API に対して null 値の許容コントラクトが正しく表現されています。</span><span class="sxs-lookup"><span data-stu-id="26140-119">The updated annotations correctly represent the nullability contracts for the APIs.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="26140-120">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="26140-120">Recommended action</span></span>

<span data-ttu-id="26140-121">これらの API を呼び出すコードを更新し、修正された null 値の許容コントラクトを反映します。</span><span class="sxs-lookup"><span data-stu-id="26140-121">Update code that calls these APIs to reflect the revised nullability contracts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="26140-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="26140-122">Affected APIs</span></span>

<span data-ttu-id="26140-123">影響を受ける API は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="26140-123">The following table lists the affected APIs:</span></span>

| <span data-ttu-id="26140-124">API</span><span class="sxs-lookup"><span data-stu-id="26140-124">API</span></span> | <span data-ttu-id="26140-125">変更箇所</span><span class="sxs-lookup"><span data-stu-id="26140-125">What changed</span></span> | <span data-ttu-id="26140-126">破壊的または非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-126">Breaking or nonbreaking</span></span> | <span data-ttu-id="26140-127">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="26140-127">Version added</span></span> |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | <span data-ttu-id="26140-128">プロパティ型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-128">Property type is nullable</span></span> | <span data-ttu-id="26140-129">あり</span><span class="sxs-lookup"><span data-stu-id="26140-129">Breaking</span></span> | <span data-ttu-id="26140-130">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-130">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-131">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-131">Parameter type is nullable</span></span> | <span data-ttu-id="26140-132">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-132">Nonbreaking</span></span> | <span data-ttu-id="26140-133">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-133">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-134">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-134">Parameter type is nullable</span></span> | <span data-ttu-id="26140-135">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-135">Nonbreaking</span></span> | <span data-ttu-id="26140-136">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-136">Preview 1</span></span> |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-137">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-137">Parameter type is nullable</span></span> | <span data-ttu-id="26140-138">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-138">Nonbreaking</span></span> | <span data-ttu-id="26140-139">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-139">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | <span data-ttu-id="26140-140">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-140">Parameter type is nullable</span></span> | <span data-ttu-id="26140-141">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-141">Nonbreaking</span></span> | <span data-ttu-id="26140-142">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-142">Preview 1</span></span> |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | <span data-ttu-id="26140-143">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-143">Parameter type is nullable</span></span> | <span data-ttu-id="26140-144">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-144">Nonbreaking</span></span> | <span data-ttu-id="26140-145">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-145">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="26140-146">2 番目のパラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-146">Second parameter type is nullable</span></span> | <span data-ttu-id="26140-147">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-147">Nonbreaking</span></span> | <span data-ttu-id="26140-148">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-148">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-149">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-149">Parameter type is nullable</span></span> | <span data-ttu-id="26140-150">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-150">Nonbreaking</span></span> | <span data-ttu-id="26140-151">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-151">Preview 1</span></span> |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-152">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-152">Parameter type is nullable</span></span> | <span data-ttu-id="26140-153">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-153">Nonbreaking</span></span> | <span data-ttu-id="26140-154">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-154">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-155">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-155">Parameter type is nullable</span></span> | <span data-ttu-id="26140-156">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-156">Nonbreaking</span></span> | <span data-ttu-id="26140-157">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-157">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-158">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-158">Parameter type is nullable</span></span> | <span data-ttu-id="26140-159">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-159">Nonbreaking</span></span> | <span data-ttu-id="26140-160">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-160">Preview 1</span></span> |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-161">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-161">Parameter type is nullable</span></span> | <span data-ttu-id="26140-162">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-162">Nonbreaking</span></span> | <span data-ttu-id="26140-163">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-163">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | <span data-ttu-id="26140-164">2 番目のパラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-164">Second parameter type is nullable</span></span> | <span data-ttu-id="26140-165">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-165">Nonbreaking</span></span> | <span data-ttu-id="26140-166">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-166">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | <span data-ttu-id="26140-167">2 番目のパラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-167">Second parameter type is nullable</span></span> | <span data-ttu-id="26140-168">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-168">Nonbreaking</span></span> | <span data-ttu-id="26140-169">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-169">Preview 1</span></span> |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | <span data-ttu-id="26140-170">パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-170">Parameter type is nullable</span></span> | <span data-ttu-id="26140-171">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-171">Nonbreaking</span></span> | <span data-ttu-id="26140-172">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-172">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="26140-173">`content` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-173">`content` parameter type is nullable</span></span> | <span data-ttu-id="26140-174">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-174">Nonbreaking</span></span> | <span data-ttu-id="26140-175">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-175">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="26140-176">`content` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-176">`content` parameter type is nullable</span></span>  | <span data-ttu-id="26140-177">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-177">Nonbreaking</span></span> | <span data-ttu-id="26140-178">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-178">Preview 1</span></span> |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | <span data-ttu-id="26140-179">`content` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-179">`content` parameter type is nullable</span></span>  | <span data-ttu-id="26140-180">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-180">Nonbreaking</span></span> | <span data-ttu-id="26140-181">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-181">Preview 1</span></span> |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | <span data-ttu-id="26140-182">1 番目のパラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-182">First parameter type is nullable</span></span> | <span data-ttu-id="26140-183">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-183">Nonbreaking</span></span> | <span data-ttu-id="26140-184">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-184">Preview 1</span></span> |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | <span data-ttu-id="26140-185">戻り値の型が null 許容ではない</span><span class="sxs-lookup"><span data-stu-id="26140-185">Return type is not nullable</span></span> | <span data-ttu-id="26140-186">非破壊的</span><span class="sxs-lookup"><span data-stu-id="26140-186">Nonbreaking</span></span> | <span data-ttu-id="26140-187">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-187">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="26140-188">`buffer` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-188">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="26140-189">あり</span><span class="sxs-lookup"><span data-stu-id="26140-189">Breaking</span></span> | <span data-ttu-id="26140-190">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-190">Preview 1</span></span> |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="26140-191">`buffer` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-191">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="26140-192">あり</span><span class="sxs-lookup"><span data-stu-id="26140-192">Breaking</span></span> | <span data-ttu-id="26140-193">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-193">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="26140-194">`buffer` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-194">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="26140-195">あり</span><span class="sxs-lookup"><span data-stu-id="26140-195">Breaking</span></span> | <span data-ttu-id="26140-196">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-196">Preview 1</span></span> |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="26140-197">`buffer` パラメーター型が null 許容に</span><span class="sxs-lookup"><span data-stu-id="26140-197">`buffer` parameter type is nullable</span></span> | <span data-ttu-id="26140-198">あり</span><span class="sxs-lookup"><span data-stu-id="26140-198">Breaking</span></span> | <span data-ttu-id="26140-199">Preview 1</span><span class="sxs-lookup"><span data-stu-id="26140-199">Preview 1</span></span> |

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->
