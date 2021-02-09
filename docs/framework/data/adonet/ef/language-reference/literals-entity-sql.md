---
description: '詳細情報: リテラル (Entity SQL)'
title: リテラル (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: cae2ec7ab8cf19166dc3100a85473fca2ed0a7be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791882"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="d6211-103">リテラル (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d6211-103">Literals (Entity SQL)</span></span>

<span data-ttu-id="d6211-104">このトピックでは、リテラルに関する [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d6211-104">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="d6211-105">Null</span><span class="sxs-lookup"><span data-stu-id="d6211-105">Null</span></span>  

 <span data-ttu-id="d6211-106">NULL リテラルは、あらゆる型で NULL 値を表す際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-106">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="d6211-107">NULL リテラルは、すべての型と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="d6211-107">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="d6211-108">NULL リテラルをキャストすることによって、型指定された NULL を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d6211-108">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="d6211-109">詳しくは、「[CAST](cast-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d6211-109">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="d6211-110">型指定されない NULL リテラルを使用できる場合に関する規則については、「[NULL リテラルと型推論](null-literals-and-type-inference-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d6211-110">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="d6211-111">ブール型</span><span class="sxs-lookup"><span data-stu-id="d6211-111">Boolean</span></span>  

 <span data-ttu-id="d6211-112">ブール型リテラルは、`true` と `false` のキーワードで表されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-112">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="d6211-113">整数型</span><span class="sxs-lookup"><span data-stu-id="d6211-113">Integer</span></span>  

 <span data-ttu-id="d6211-114">整数リテラルには、<xref:System.Int32> 型と <xref:System.Int64> 型とがあります。</span><span class="sxs-lookup"><span data-stu-id="d6211-114">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="d6211-115"><xref:System.Int32> リテラルは、一連の数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-115">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="d6211-116"><xref:System.Int64> リテラルは、一連の数字で構成され、最後に大文字の L が付きます。</span><span class="sxs-lookup"><span data-stu-id="d6211-116">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="d6211-117">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="d6211-117">Decimal</span></span>  

 <span data-ttu-id="d6211-118">固定小数点数 (decimal) は、一連の数字、ドット (.)、および別の一連の数字で構成され、最後に大文字の "M" が付きます。</span><span class="sxs-lookup"><span data-stu-id="d6211-118">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="d6211-119">Float、Double</span><span class="sxs-lookup"><span data-stu-id="d6211-119">Float, Double</span></span>  

 <span data-ttu-id="d6211-120">倍精度浮動小数点数は、一連の数字、ドット (.)、および別の一連の数字で構成され、場合によっては最後に指数が付きます。</span><span class="sxs-lookup"><span data-stu-id="d6211-120">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="d6211-121">単精度浮動小数点数 (float) は、倍精度浮動小数点数の構文に続けて小文字の f が付きます。</span><span class="sxs-lookup"><span data-stu-id="d6211-121">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="d6211-122">String</span><span class="sxs-lookup"><span data-stu-id="d6211-122">String</span></span>  

 <span data-ttu-id="d6211-123">文字列は、引用符で囲まれた一連の文字です。</span><span class="sxs-lookup"><span data-stu-id="d6211-123">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="d6211-124">引用符には、単一引用符 (`'`) または二重引用符 (") を使用できますが、両者を混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="d6211-124">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="d6211-125">文字列リテラルには、Unicode と非 Unicode のどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6211-125">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="d6211-126">文字列リテラルを Unicode として宣言するには、リテラルの前に大文字の "N" を付けます。</span><span class="sxs-lookup"><span data-stu-id="d6211-126">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="d6211-127">既定では、Unicode でない文字列リテラルです。</span><span class="sxs-lookup"><span data-stu-id="d6211-127">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="d6211-128">N と文字列リテラルの間に空白は含めません。また、N は大文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6211-128">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="d6211-129">DateTime</span><span class="sxs-lookup"><span data-stu-id="d6211-129">DateTime</span></span>  

 <span data-ttu-id="d6211-130">datetime リテラルは、日付部分と時刻部分とで構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="d6211-130">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="d6211-131">日付部分と時刻部分のどちらも省略することはできず、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="d6211-131">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="d6211-132">日付部分は、`YYYY`-`MM`-`DD` という形式になっている必要があります。`YYYY` は 0001 から 9999 の 4 桁の年、`MM` は 1 から 12 の月、`DD` は特定の月 (`MM`) に対して有効な日を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-132">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="d6211-133">時刻部分は `HH`:`MM`[:`SS`[.fffffff]] の形式にする必要があります。ここで、`HH` は 0 ～ 23 時の値、`MM` は 0 ～ 59 分の値、`SS` は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-133">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="d6211-134">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="d6211-134">All value ranges are inclusive.</span></span> <span data-ttu-id="d6211-135">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d6211-135">Fractional seconds are optional.</span></span> <span data-ttu-id="d6211-136">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="d6211-136">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="d6211-137">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-137">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="d6211-138">DATETIME 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="d6211-138">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="d6211-139">時刻</span><span class="sxs-lookup"><span data-stu-id="d6211-139">Time</span></span>  

 <span data-ttu-id="d6211-140">time リテラルは、時刻部分のみで構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="d6211-140">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="d6211-141">時刻部分は必須で、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="d6211-141">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="d6211-142">時刻部分は HH:MM[:SS[.fffffff]] の形式にする必要があります。ここで、HH は 0 ～ 23 時の値、MM は 0 ～ 59 分の値、SS は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-142">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="d6211-143">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="d6211-143">All value ranges are inclusive.</span></span> <span data-ttu-id="d6211-144">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d6211-144">Fractional seconds are optional.</span></span> <span data-ttu-id="d6211-145">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="d6211-145">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="d6211-146">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-146">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="d6211-147">TIME 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="d6211-147">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="d6211-148">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="d6211-148">DateTimeOffset</span></span>  

 <span data-ttu-id="d6211-149">datetimeoffset リテラルは、日付部分、時刻部分、およびオフセット部分で構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="d6211-149">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="d6211-150">日付部分、時刻部分、オフセット部分はすべて必須で、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="d6211-150">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="d6211-151">日付部分は YYYY-MM-DD の形式にする必要があります。ここで、YYYY は 0001 ～ 9999 の 4 桁の年、MM は 1 ～ 12 の月、DD は特定の月の有効な日付を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-151">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="d6211-152">時刻部分は HH:MM[:SS[.fffffff]] の形式にする必要があります。ここで、HH は 0 ～ 23 時の値、MM は 0 ～ 59 分の値、SS は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-152">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="d6211-153">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="d6211-153">All value ranges are inclusive.</span></span> <span data-ttu-id="d6211-154">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d6211-154">Fractional seconds are optional.</span></span> <span data-ttu-id="d6211-155">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="d6211-155">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="d6211-156">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-156">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="d6211-157">オフセット部分は、{+&#124;-}HH:MM の形式にする必要があります。ここで、HH と MM は時刻部分と同じ意味です。</span><span class="sxs-lookup"><span data-stu-id="d6211-157">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="d6211-158">オフセットの範囲は -14:00 ～ + 14:00 でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d6211-158">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="d6211-159">DATETIMEOFFSET 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="d6211-159">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="d6211-160">有効な Entity SQL リテラル値は、CLR またはデータ ソースに対してサポートされている範囲に含まれないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d6211-160">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="d6211-161">その結果、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d6211-161">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="d6211-162">2 項</span><span class="sxs-lookup"><span data-stu-id="d6211-162">Binary</span></span>  

 <span data-ttu-id="d6211-163">バイナリ文字列リテラルは、binary キーワードあるいは簡略記号 `X` または `x` と、それに続く単一引用符で囲まれた一連の 16 進数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-163">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="d6211-164">簡略記号 `X` は、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="d6211-164">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="d6211-165">キーワード `binary` と、バイナリ文字列値との間には、0 個以上の空白文字が許容されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-165">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="d6211-166">16 進文字についても、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="d6211-166">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="d6211-167">リテラルが奇数個の 16 進数字で構成されていた場合、桁数が次に大きな偶数個となるように、先頭に 16 進数の 0 を付けることによって調整されます。</span><span class="sxs-lookup"><span data-stu-id="d6211-167">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="d6211-168">バイナリ文字列にサイズの制限はありません。</span><span class="sxs-lookup"><span data-stu-id="d6211-168">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="d6211-169">GUID</span><span class="sxs-lookup"><span data-stu-id="d6211-169">Guid</span></span>  

 <span data-ttu-id="d6211-170">`GUID` リテラルは、グローバル一意識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="d6211-170">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="d6211-171">キーワード `GUID` の後に、"*レジストリ*" 形式と呼ばれる次のような形式の 16 進数字が続きます: 単一引用符で囲まれた 8-4-4-4-12。</span><span class="sxs-lookup"><span data-stu-id="d6211-171">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="d6211-172">16 進数字の大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="d6211-172">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="d6211-173">GUID 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="d6211-173">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6211-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6211-174">See also</span></span>

- [<span data-ttu-id="d6211-175">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="d6211-175">Entity SQL Overview</span></span>](entity-sql-overview.md)
