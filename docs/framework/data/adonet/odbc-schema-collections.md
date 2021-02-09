---
description: '詳細情報: ODBC スキーマ コレクション'
title: ODBC スキーマ コレクション
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ceac67e49914db7010e315a2dfcdb630bea1e29f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786200"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="ff25c-103">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="ff25c-103">ODBC Schema Collections</span></span>

<span data-ttu-id="ff25c-104">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ff25c-104">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="ff25c-105">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="ff25c-105">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="ff25c-106">Microsoft SQL Server ODBC Driver では、共通のスキーマ コレクションに加えて次のスキーマ コレクションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff25c-106">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ff25c-107">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="ff25c-107">Tables</span></span>

- <span data-ttu-id="ff25c-108">Indexes</span><span class="sxs-lookup"><span data-stu-id="ff25c-108">Indexes</span></span>

- <span data-ttu-id="ff25c-109">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-109">Columns</span></span>

- <span data-ttu-id="ff25c-110">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-110">Procedures</span></span>

- <span data-ttu-id="ff25c-111">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-111">ProcedureColumns</span></span>

- <span data-ttu-id="ff25c-112">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ff25c-112">ProcedureParameters</span></span>

- <span data-ttu-id="ff25c-113">Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-113">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ff25c-114">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-114">Tables and Views</span></span>

|<span data-ttu-id="ff25c-115">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-115">ColumnName</span></span>|<span data-ttu-id="ff25c-116">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-116">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-117">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-117">TABLE_CAT</span></span>|<span data-ttu-id="ff25c-118">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-118">String</span></span>|
|<span data-ttu-id="ff25c-119">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-119">TABLE_SCHEM</span></span>|<span data-ttu-id="ff25c-120">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-120">String</span></span>|
|<span data-ttu-id="ff25c-121">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-121">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-122">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-122">String</span></span>|
|<span data-ttu-id="ff25c-123">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-123">TABLE_TYPE</span></span>|<span data-ttu-id="ff25c-124">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-124">String</span></span>|
|<span data-ttu-id="ff25c-125">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-125">REMARKS</span></span>|<span data-ttu-id="ff25c-126">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-126">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="ff25c-127">Indexes</span><span class="sxs-lookup"><span data-stu-id="ff25c-127">Indexes</span></span>

|<span data-ttu-id="ff25c-128">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-128">ColumnName</span></span>|<span data-ttu-id="ff25c-129">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-129">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-130">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-130">TABLE_CAT</span></span>|<span data-ttu-id="ff25c-131">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-131">String</span></span>|
|<span data-ttu-id="ff25c-132">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-132">TABLE_SCHEM</span></span>|<span data-ttu-id="ff25c-133">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-133">String</span></span>|
|<span data-ttu-id="ff25c-134">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-134">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-135">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-135">String</span></span>|
|<span data-ttu-id="ff25c-136">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ff25c-136">NON_UNIQUE</span></span>|<span data-ttu-id="ff25c-137">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-137">Int16</span></span>|
|<span data-ttu-id="ff25c-138">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-138">INDEX_QUALIFIER</span></span>|<span data-ttu-id="ff25c-139">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-139">String</span></span>|
|<span data-ttu-id="ff25c-140">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-140">INDEX_NAME</span></span>|<span data-ttu-id="ff25c-141">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-141">String</span></span>|
|<span data-ttu-id="ff25c-142">TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-142">TYPE</span></span>|<span data-ttu-id="ff25c-143">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-143">Int16</span></span>|
|<span data-ttu-id="ff25c-144">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-144">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-145">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-145">Int16</span></span>|
|<span data-ttu-id="ff25c-146">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-146">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-147">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-147">String</span></span>|
|<span data-ttu-id="ff25c-148">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="ff25c-148">ASC_OR_DESC</span></span>|<span data-ttu-id="ff25c-149">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-149">String</span></span>|
|<span data-ttu-id="ff25c-150">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="ff25c-150">CARDINALITY</span></span>|<span data-ttu-id="ff25c-151">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-151">Int32</span></span>|
|<span data-ttu-id="ff25c-152">PAGES</span><span class="sxs-lookup"><span data-stu-id="ff25c-152">PAGES</span></span>|<span data-ttu-id="ff25c-153">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-153">Int32</span></span>|
|<span data-ttu-id="ff25c-154">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-154">FILTER_CONDITION</span></span>|<span data-ttu-id="ff25c-155">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-155">String</span></span>|
|<span data-ttu-id="ff25c-156">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ff25c-156">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ff25c-157">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-157">String</span></span>|
|<span data-ttu-id="ff25c-158">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-158">SS_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-159">Byte</span><span class="sxs-lookup"><span data-stu-id="ff25c-159">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="ff25c-160">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-160">Columns</span></span>

|<span data-ttu-id="ff25c-161">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-161">ColumnName</span></span>|<span data-ttu-id="ff25c-162">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-162">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-163">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-163">TABLE_CAT</span></span>|<span data-ttu-id="ff25c-164">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-164">String</span></span>|
|<span data-ttu-id="ff25c-165">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-165">TABLE_SCHEM</span></span>|<span data-ttu-id="ff25c-166">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-166">String</span></span>|
|<span data-ttu-id="ff25c-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-167">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-168">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-168">String</span></span>|
|<span data-ttu-id="ff25c-169">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-169">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-170">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-170">String</span></span>|
|<span data-ttu-id="ff25c-171">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-171">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-172">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-172">Int16</span></span>|
|<span data-ttu-id="ff25c-173">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-173">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-174">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-174">String</span></span>|
|<span data-ttu-id="ff25c-175">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ff25c-175">COLUMN_SIZE</span></span>|<span data-ttu-id="ff25c-176">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-176">Int32</span></span>|
|<span data-ttu-id="ff25c-177">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-177">BUFFER_LENGTH</span></span>|<span data-ttu-id="ff25c-178">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-178">Int32</span></span>|
|<span data-ttu-id="ff25c-179">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ff25c-179">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ff25c-180">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-180">Int16</span></span>|
|<span data-ttu-id="ff25c-181">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-181">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ff25c-182">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-182">Int16</span></span>|
|<span data-ttu-id="ff25c-183">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-183">NULLABLE</span></span>|<span data-ttu-id="ff25c-184">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-184">Int16</span></span>|
|<span data-ttu-id="ff25c-185">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-185">REMARKS</span></span>|<span data-ttu-id="ff25c-186">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-186">String</span></span>|
|<span data-ttu-id="ff25c-187">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ff25c-187">COLUMN_DEF</span></span>|<span data-ttu-id="ff25c-188">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-188">String</span></span>|
|<span data-ttu-id="ff25c-189">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-189">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-190">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-190">Int16</span></span>|
|<span data-ttu-id="ff25c-191">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ff25c-191">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ff25c-192">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-192">Int16</span></span>|
|<span data-ttu-id="ff25c-193">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-193">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ff25c-194">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-194">Int32</span></span>|
|<span data-ttu-id="ff25c-195">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-195">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-196">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-196">Int32</span></span>|
|<span data-ttu-id="ff25c-197">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-197">IS_NULLABLE</span></span>|<span data-ttu-id="ff25c-198">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-198">String</span></span>|
|<span data-ttu-id="ff25c-199">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ff25c-199">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ff25c-200">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-200">String</span></span>|
|<span data-ttu-id="ff25c-201">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ff25c-201">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ff25c-202">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-202">String</span></span>|
|<span data-ttu-id="ff25c-203">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-203">SS_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-204">Byte</span><span class="sxs-lookup"><span data-stu-id="ff25c-204">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="ff25c-205">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-205">Procedures</span></span>

|<span data-ttu-id="ff25c-206">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-206">ColumnName</span></span>|<span data-ttu-id="ff25c-207">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-207">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-208">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-208">PROCEDURE_CAT</span></span>|<span data-ttu-id="ff25c-209">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-209">String</span></span>|
|<span data-ttu-id="ff25c-210">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-210">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ff25c-211">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-211">String</span></span>|
|<span data-ttu-id="ff25c-212">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-212">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-213">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-213">String</span></span>|
|<span data-ttu-id="ff25c-214">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-214">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-215">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-215">Int32</span></span>|
|<span data-ttu-id="ff25c-216">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-216">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-217">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-217">Int32</span></span>|
|<span data-ttu-id="ff25c-218">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ff25c-218">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ff25c-219">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-219">Int32</span></span>|
|<span data-ttu-id="ff25c-220">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-220">REMARKS</span></span>|<span data-ttu-id="ff25c-221">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-221">String</span></span>|
|<span data-ttu-id="ff25c-222">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-222">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ff25c-223">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-223">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ff25c-224">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-224">ProcedureColumns</span></span>

|<span data-ttu-id="ff25c-225">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-225">ColumnName</span></span>|<span data-ttu-id="ff25c-226">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-226">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-227">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-227">PROCEDURE_CAT</span></span>|<span data-ttu-id="ff25c-228">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-228">String</span></span>|
|<span data-ttu-id="ff25c-229">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-229">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ff25c-230">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-230">String</span></span>|
|<span data-ttu-id="ff25c-231">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-231">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-232">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-232">String</span></span>|
|<span data-ttu-id="ff25c-233">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-233">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-234">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-234">String</span></span>|
|<span data-ttu-id="ff25c-235">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-235">COLUMN_TYPE</span></span>|<span data-ttu-id="ff25c-236">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-236">Int16</span></span>|
|<span data-ttu-id="ff25c-237">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-237">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-238">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-238">Int16</span></span>|
|<span data-ttu-id="ff25c-239">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-239">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-240">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-240">String</span></span>|
|<span data-ttu-id="ff25c-241">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ff25c-241">COLUMN_SIZE</span></span>|<span data-ttu-id="ff25c-242">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-242">Int32</span></span>|
|<span data-ttu-id="ff25c-243">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-243">BUFFER_LENGTH</span></span>|<span data-ttu-id="ff25c-244">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-244">Int32</span></span>|
|<span data-ttu-id="ff25c-245">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ff25c-245">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ff25c-246">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-246">Int16</span></span>|
|<span data-ttu-id="ff25c-247">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-247">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ff25c-248">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-248">Int16</span></span>|
|<span data-ttu-id="ff25c-249">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-249">NULLABLE</span></span>|<span data-ttu-id="ff25c-250">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-250">Int16</span></span>|
|<span data-ttu-id="ff25c-251">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-251">REMARKS</span></span>|<span data-ttu-id="ff25c-252">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-252">String</span></span>|
|<span data-ttu-id="ff25c-253">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ff25c-253">COLUMN_DEF</span></span>|<span data-ttu-id="ff25c-254">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-254">String</span></span>|
|<span data-ttu-id="ff25c-255">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-255">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-256">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-256">Int16</span></span>|
|<span data-ttu-id="ff25c-257">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ff25c-257">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ff25c-258">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-258">Int16</span></span>|
|<span data-ttu-id="ff25c-259">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-259">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ff25c-260">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-260">Int32</span></span>|
|<span data-ttu-id="ff25c-261">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-261">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-262">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-262">Int32</span></span>|
|<span data-ttu-id="ff25c-263">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-263">IS_NULLABLE</span></span>|<span data-ttu-id="ff25c-264">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-264">String</span></span>|
|<span data-ttu-id="ff25c-265">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ff25c-265">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ff25c-266">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-266">String</span></span>|
|<span data-ttu-id="ff25c-267">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ff25c-267">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ff25c-268">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-268">String</span></span>|
|<span data-ttu-id="ff25c-269">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-269">SS_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-270">Byte</span><span class="sxs-lookup"><span data-stu-id="ff25c-270">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="ff25c-271">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ff25c-271">ProcedureParameters</span></span>

|<span data-ttu-id="ff25c-272">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-272">ColumnName</span></span>|<span data-ttu-id="ff25c-273">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-273">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-274">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-274">PROCEDURE_CAT</span></span>|<span data-ttu-id="ff25c-275">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-275">String</span></span>|
|<span data-ttu-id="ff25c-276">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-276">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ff25c-277">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-277">String</span></span>|
|<span data-ttu-id="ff25c-278">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-278">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-279">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-279">String</span></span>|
|<span data-ttu-id="ff25c-280">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-280">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-281">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-281">String</span></span>|
|<span data-ttu-id="ff25c-282">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-282">COLUMN_TYPE</span></span>|<span data-ttu-id="ff25c-283">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-283">Int16</span></span>|
|<span data-ttu-id="ff25c-284">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-284">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-285">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-285">Int16</span></span>|
|<span data-ttu-id="ff25c-286">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-286">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-287">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-287">String</span></span>|
|<span data-ttu-id="ff25c-288">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ff25c-288">COLUMN_SIZE</span></span>|<span data-ttu-id="ff25c-289">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-289">Int32</span></span>|
|<span data-ttu-id="ff25c-290">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-290">BUFFER_LENGTH</span></span>|<span data-ttu-id="ff25c-291">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-291">Int32</span></span>|
|<span data-ttu-id="ff25c-292">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ff25c-292">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ff25c-293">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-293">Int16</span></span>|
|<span data-ttu-id="ff25c-294">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-294">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ff25c-295">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-295">Int16</span></span>|
|<span data-ttu-id="ff25c-296">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-296">NULLABLE</span></span>|<span data-ttu-id="ff25c-297">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-297">Int16</span></span>|
|<span data-ttu-id="ff25c-298">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-298">REMARKS</span></span>|<span data-ttu-id="ff25c-299">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-299">String</span></span>|
|<span data-ttu-id="ff25c-300">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ff25c-300">COLUMN_DEF</span></span>|<span data-ttu-id="ff25c-301">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-301">String</span></span>|
|<span data-ttu-id="ff25c-302">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-302">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-303">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-303">Int16</span></span>|
|<span data-ttu-id="ff25c-304">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ff25c-304">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ff25c-305">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-305">Int16</span></span>|
|<span data-ttu-id="ff25c-306">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-306">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ff25c-307">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-307">Int32</span></span>|
|<span data-ttu-id="ff25c-308">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-308">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-309">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-309">Int32</span></span>|
|<span data-ttu-id="ff25c-310">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-310">IS_NULLABLE</span></span>|<span data-ttu-id="ff25c-311">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-311">String</span></span>|
|<span data-ttu-id="ff25c-312">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ff25c-312">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ff25c-313">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-313">String</span></span>|
|<span data-ttu-id="ff25c-314">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ff25c-314">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ff25c-315">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-315">String</span></span>|
|<span data-ttu-id="ff25c-316">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-316">SS_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-317">Byte</span><span class="sxs-lookup"><span data-stu-id="ff25c-317">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="ff25c-318">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="ff25c-318">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="ff25c-319">Microsoft SQL Server Oracle ODBC Driver では、共通のスキーマ コレクションに加えて次のスキーマ コレクションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff25c-319">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ff25c-320">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="ff25c-320">Tables</span></span>

- <span data-ttu-id="ff25c-321">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-321">Columns</span></span>

- <span data-ttu-id="ff25c-322">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-322">Procedures</span></span>

- <span data-ttu-id="ff25c-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-323">ProcedureColumns</span></span>

- <span data-ttu-id="ff25c-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ff25c-324">ProcedureParameters</span></span>

- <span data-ttu-id="ff25c-325">Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-325">Views</span></span>

- <span data-ttu-id="ff25c-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="ff25c-326">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ff25c-327">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-327">Tables and Views</span></span>

|<span data-ttu-id="ff25c-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-328">ColumnName</span></span>|<span data-ttu-id="ff25c-329">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-329">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-330">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-330">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-331">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-331">String</span></span>|
|<span data-ttu-id="ff25c-332">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-332">TABLE_OWNER</span></span>|<span data-ttu-id="ff25c-333">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-333">String</span></span>|
|<span data-ttu-id="ff25c-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-334">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-335">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-335">String</span></span>|
|<span data-ttu-id="ff25c-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-336">TABLE_TYPE</span></span>|<span data-ttu-id="ff25c-337">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-337">String</span></span>|
|<span data-ttu-id="ff25c-338">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-338">REMARKS</span></span>|<span data-ttu-id="ff25c-339">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-339">String</span></span>|

### <a name="columns"></a><span data-ttu-id="ff25c-340">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-340">Columns</span></span>

|<span data-ttu-id="ff25c-341">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-341">ColumnName</span></span>|<span data-ttu-id="ff25c-342">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-342">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-343">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-343">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-344">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-344">String</span></span>|
|<span data-ttu-id="ff25c-345">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-345">TABLE_OWNER</span></span>|<span data-ttu-id="ff25c-346">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-346">String</span></span>|
|<span data-ttu-id="ff25c-347">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-347">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-348">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-348">String</span></span>|
|<span data-ttu-id="ff25c-349">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-349">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-350">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-350">String</span></span>|
|<span data-ttu-id="ff25c-351">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-351">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-352">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-352">Int16</span></span>|
|<span data-ttu-id="ff25c-353">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-353">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-354">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-354">String</span></span>|
|<span data-ttu-id="ff25c-355">PRECISION</span><span class="sxs-lookup"><span data-stu-id="ff25c-355">PRECISION</span></span>|<span data-ttu-id="ff25c-356">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-356">Int32</span></span>|
|<span data-ttu-id="ff25c-357">LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-357">LENGTH</span></span>|<span data-ttu-id="ff25c-358">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-358">Int32</span></span>|
|<span data-ttu-id="ff25c-359">SCALE</span><span class="sxs-lookup"><span data-stu-id="ff25c-359">SCALE</span></span>|<span data-ttu-id="ff25c-360">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-360">Int16</span></span>|
|<span data-ttu-id="ff25c-361">RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-361">RADIX</span></span>|<span data-ttu-id="ff25c-362">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-362">Int16</span></span>|
|<span data-ttu-id="ff25c-363">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-363">NULLABLE</span></span>|<span data-ttu-id="ff25c-364">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-364">Int16</span></span>|
|<span data-ttu-id="ff25c-365">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-365">REMARKS</span></span>|<span data-ttu-id="ff25c-366">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-366">String</span></span>|
|<span data-ttu-id="ff25c-367">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-367">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-368">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-368">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="ff25c-369">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-369">Procedures</span></span>

|<span data-ttu-id="ff25c-370">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-370">ColumnName</span></span>|<span data-ttu-id="ff25c-371">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-371">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-372">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-372">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-373">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-373">String</span></span>|
|<span data-ttu-id="ff25c-374">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-374">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ff25c-375">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-375">String</span></span>|
|<span data-ttu-id="ff25c-376">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-376">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-377">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-377">String</span></span>|
|<span data-ttu-id="ff25c-378">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-378">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-379">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-379">Int16</span></span>|
|<span data-ttu-id="ff25c-380">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-380">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-381">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-381">Int16</span></span>|
|<span data-ttu-id="ff25c-382">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ff25c-382">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ff25c-383">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-383">Int16</span></span>|
|<span data-ttu-id="ff25c-384">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-384">REMARKS</span></span>|<span data-ttu-id="ff25c-385">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-385">String</span></span>|
|<span data-ttu-id="ff25c-386">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-386">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ff25c-387">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-387">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ff25c-388">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-388">ProcedureColumns</span></span>

|<span data-ttu-id="ff25c-389">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-389">ColumnName</span></span>|<span data-ttu-id="ff25c-390">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-390">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-391">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-391">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-392">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-392">String</span></span>|
|<span data-ttu-id="ff25c-393">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-393">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ff25c-394">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-394">String</span></span>|
|<span data-ttu-id="ff25c-395">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-395">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-396">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-396">String</span></span>|
|<span data-ttu-id="ff25c-397">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-397">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-398">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-398">String</span></span>|
|<span data-ttu-id="ff25c-399">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-399">COLUMN_TYPE</span></span>|<span data-ttu-id="ff25c-400">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-400">Int16</span></span>|
|<span data-ttu-id="ff25c-401">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-401">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-402">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-402">Int16</span></span>|
|<span data-ttu-id="ff25c-403">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-403">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-404">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-404">String</span></span>|
|<span data-ttu-id="ff25c-405">PRECISION</span><span class="sxs-lookup"><span data-stu-id="ff25c-405">PRECISION</span></span>|<span data-ttu-id="ff25c-406">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-406">Int32</span></span>|
|<span data-ttu-id="ff25c-407">LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-407">LENGTH</span></span>|<span data-ttu-id="ff25c-408">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-408">Int32</span></span>|
|<span data-ttu-id="ff25c-409">SCALE</span><span class="sxs-lookup"><span data-stu-id="ff25c-409">SCALE</span></span>|<span data-ttu-id="ff25c-410">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-410">Int16</span></span>|
|<span data-ttu-id="ff25c-411">RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-411">RADIX</span></span>|<span data-ttu-id="ff25c-412">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-412">Int16</span></span>|
|<span data-ttu-id="ff25c-413">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-413">NULLABLE</span></span>|<span data-ttu-id="ff25c-414">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-414">Int16</span></span>|
|<span data-ttu-id="ff25c-415">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-415">REMARKS</span></span>|<span data-ttu-id="ff25c-416">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-416">String</span></span>|
|<span data-ttu-id="ff25c-417">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="ff25c-417">OVERLOAD</span></span>|<span data-ttu-id="ff25c-418">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-418">Int32</span></span>|
|<span data-ttu-id="ff25c-419">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-419">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-420">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-420">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="ff25c-421">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="ff25c-421">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="ff25c-422">Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ff25c-422">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ff25c-423">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="ff25c-423">Tables</span></span>

- <span data-ttu-id="ff25c-424">Indexes</span><span class="sxs-lookup"><span data-stu-id="ff25c-424">Indexes</span></span>

- <span data-ttu-id="ff25c-425">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-425">Columns</span></span>

- <span data-ttu-id="ff25c-426">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-426">Procedures</span></span>

- <span data-ttu-id="ff25c-427">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-427">ProcedureColumns</span></span>

- <span data-ttu-id="ff25c-428">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ff25c-428">ProcedureParameters</span></span>

- <span data-ttu-id="ff25c-429">Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-429">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ff25c-430">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="ff25c-430">Tables and Views</span></span>

|<span data-ttu-id="ff25c-431">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-431">ColumnName</span></span>|<span data-ttu-id="ff25c-432">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-432">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-433">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-433">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-434">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-434">String</span></span>|
|<span data-ttu-id="ff25c-435">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-435">TABLE_OWNER</span></span>|<span data-ttu-id="ff25c-436">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-436">String</span></span>|
|<span data-ttu-id="ff25c-437">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-437">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-438">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-438">String</span></span>|
|<span data-ttu-id="ff25c-439">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-439">TABLE_TYPE</span></span>|<span data-ttu-id="ff25c-440">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-440">String</span></span>|
|<span data-ttu-id="ff25c-441">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-441">REMARKS</span></span>|<span data-ttu-id="ff25c-442">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-442">String</span></span>|

### <a name="columns"></a><span data-ttu-id="ff25c-443">列</span><span class="sxs-lookup"><span data-stu-id="ff25c-443">Columns</span></span>

|<span data-ttu-id="ff25c-444">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-444">ColumnName</span></span>|<span data-ttu-id="ff25c-445">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-445">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-446">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-446">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-447">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-447">String</span></span>|
|<span data-ttu-id="ff25c-448">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-448">TABLE_OWNER</span></span>|<span data-ttu-id="ff25c-449">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-449">String</span></span>|
|<span data-ttu-id="ff25c-450">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-450">TABLE_NAME</span></span>|<span data-ttu-id="ff25c-451">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-451">String</span></span>|
|<span data-ttu-id="ff25c-452">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-452">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-453">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-453">String</span></span>|
|<span data-ttu-id="ff25c-454">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-454">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-455">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-455">Int16</span></span>|
|<span data-ttu-id="ff25c-456">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-456">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-457">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-457">String</span></span>|
|<span data-ttu-id="ff25c-458">PRECISION</span><span class="sxs-lookup"><span data-stu-id="ff25c-458">PRECISION</span></span>|<span data-ttu-id="ff25c-459">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-459">Int32</span></span>|
|<span data-ttu-id="ff25c-460">LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-460">LENGTH</span></span>|<span data-ttu-id="ff25c-461">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-461">Int32</span></span>|
|<span data-ttu-id="ff25c-462">SCALE</span><span class="sxs-lookup"><span data-stu-id="ff25c-462">SCALE</span></span>|<span data-ttu-id="ff25c-463">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-463">Int16</span></span>|
|<span data-ttu-id="ff25c-464">RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-464">RADIX</span></span>|<span data-ttu-id="ff25c-465">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-465">Int16</span></span>|
|<span data-ttu-id="ff25c-466">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-466">NULLABLE</span></span>|<span data-ttu-id="ff25c-467">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-467">Int16</span></span>|
|<span data-ttu-id="ff25c-468">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-468">REMARKS</span></span>|<span data-ttu-id="ff25c-469">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-469">String</span></span>|
|<span data-ttu-id="ff25c-470">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-470">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-471">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-471">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="ff25c-472">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ff25c-472">Procedures</span></span>

|<span data-ttu-id="ff25c-473">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-473">ColumnName</span></span>|<span data-ttu-id="ff25c-474">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-474">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-475">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-475">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-476">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-476">String</span></span>|
|<span data-ttu-id="ff25c-477">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-477">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ff25c-478">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-478">String</span></span>|
|<span data-ttu-id="ff25c-479">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-479">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-480">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-480">String</span></span>|
|<span data-ttu-id="ff25c-481">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-481">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-482">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-482">Int16</span></span>|
|<span data-ttu-id="ff25c-483">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ff25c-483">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ff25c-484">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-484">Int16</span></span>|
|<span data-ttu-id="ff25c-485">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ff25c-485">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ff25c-486">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-486">Int16</span></span>|
|<span data-ttu-id="ff25c-487">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-487">REMARKS</span></span>|<span data-ttu-id="ff25c-488">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-488">String</span></span>|
|<span data-ttu-id="ff25c-489">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-489">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ff25c-490">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-490">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ff25c-491">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ff25c-491">ProcedureColumns</span></span>

|<span data-ttu-id="ff25c-492">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-492">ColumnName</span></span>|<span data-ttu-id="ff25c-493">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-493">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-494">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ff25c-494">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ff25c-495">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-495">String</span></span>|
|<span data-ttu-id="ff25c-496">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff25c-496">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ff25c-497">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-497">String</span></span>|
|<span data-ttu-id="ff25c-498">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-498">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-499">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-499">String</span></span>|
|<span data-ttu-id="ff25c-500">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-500">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-501">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-501">String</span></span>|
|<span data-ttu-id="ff25c-502">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-502">COLUMN_TYPE</span></span>|<span data-ttu-id="ff25c-503">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-503">Int16</span></span>|
|<span data-ttu-id="ff25c-504">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-504">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-505">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-505">Int16</span></span>|
|<span data-ttu-id="ff25c-506">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-506">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-507">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-507">String</span></span>|
|<span data-ttu-id="ff25c-508">PRECISION</span><span class="sxs-lookup"><span data-stu-id="ff25c-508">PRECISION</span></span>|<span data-ttu-id="ff25c-509">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-509">Int32</span></span>|
|<span data-ttu-id="ff25c-510">LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-510">LENGTH</span></span>|<span data-ttu-id="ff25c-511">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-511">Int32</span></span>|
|<span data-ttu-id="ff25c-512">SCALE</span><span class="sxs-lookup"><span data-stu-id="ff25c-512">SCALE</span></span>|<span data-ttu-id="ff25c-513">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-513">Int16</span></span>|
|<span data-ttu-id="ff25c-514">RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-514">RADIX</span></span>|<span data-ttu-id="ff25c-515">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-515">Int16</span></span>|
|<span data-ttu-id="ff25c-516">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-516">NULLABLE</span></span>|<span data-ttu-id="ff25c-517">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-517">Int16</span></span>|
|<span data-ttu-id="ff25c-518">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-518">REMARKS</span></span>|<span data-ttu-id="ff25c-519">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-519">String</span></span>|
|<span data-ttu-id="ff25c-520">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="ff25c-520">OVERLOAD</span></span>|<span data-ttu-id="ff25c-521">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-521">Int32</span></span>|
|<span data-ttu-id="ff25c-522">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-522">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-523">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-523">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="ff25c-524">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ff25c-524">ProcedureParameters</span></span>

|<span data-ttu-id="ff25c-525">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ff25c-525">ColumnName</span></span>|<span data-ttu-id="ff25c-526">DataType</span><span class="sxs-lookup"><span data-stu-id="ff25c-526">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ff25c-527">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ff25c-527">PROCEDURE_CAT</span></span>|<span data-ttu-id="ff25c-528">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-528">String</span></span>|
|<span data-ttu-id="ff25c-529">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ff25c-529">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ff25c-530">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-530">String</span></span>|
|<span data-ttu-id="ff25c-531">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-531">PROCEDURE_NAME</span></span>|<span data-ttu-id="ff25c-532">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-532">String</span></span>|
|<span data-ttu-id="ff25c-533">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-533">COLUMN_NAME</span></span>|<span data-ttu-id="ff25c-534">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-534">String</span></span>|
|<span data-ttu-id="ff25c-535">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-535">COLUMN_TYPE</span></span>|<span data-ttu-id="ff25c-536">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-536">Int16</span></span>|
|<span data-ttu-id="ff25c-537">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-537">DATA_TYPE</span></span>|<span data-ttu-id="ff25c-538">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-538">Int16</span></span>|
|<span data-ttu-id="ff25c-539">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ff25c-539">TYPE_NAME</span></span>|<span data-ttu-id="ff25c-540">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-540">String</span></span>|
|<span data-ttu-id="ff25c-541">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ff25c-541">COLUMN_SIZE</span></span>|<span data-ttu-id="ff25c-542">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-542">Int32</span></span>|
|<span data-ttu-id="ff25c-543">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-543">BUFFER_LENGTH</span></span>|<span data-ttu-id="ff25c-544">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-544">Int32</span></span>|
|<span data-ttu-id="ff25c-545">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ff25c-545">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ff25c-546">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-546">Int16</span></span>|
|<span data-ttu-id="ff25c-547">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ff25c-547">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ff25c-548">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-548">Int16</span></span>|
|<span data-ttu-id="ff25c-549">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-549">NULLABLE</span></span>|<span data-ttu-id="ff25c-550">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-550">Int16</span></span>|
|<span data-ttu-id="ff25c-551">REMARKS</span><span class="sxs-lookup"><span data-stu-id="ff25c-551">REMARKS</span></span>|<span data-ttu-id="ff25c-552">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-552">String</span></span>|
|<span data-ttu-id="ff25c-553">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ff25c-553">COLUMN_DEF</span></span>|<span data-ttu-id="ff25c-554">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-554">String</span></span>|
|<span data-ttu-id="ff25c-555">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ff25c-555">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ff25c-556">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-556">Int16</span></span>|
|<span data-ttu-id="ff25c-557">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ff25c-557">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ff25c-558">Int16</span><span class="sxs-lookup"><span data-stu-id="ff25c-558">Int16</span></span>|
|<span data-ttu-id="ff25c-559">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ff25c-559">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ff25c-560">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-560">Int32</span></span>|
|<span data-ttu-id="ff25c-561">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ff25c-561">ORDINAL_POSITION</span></span>|<span data-ttu-id="ff25c-562">Int32</span><span class="sxs-lookup"><span data-stu-id="ff25c-562">Int32</span></span>|
|<span data-ttu-id="ff25c-563">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ff25c-563">IS_NULLABLE</span></span>|<span data-ttu-id="ff25c-564">String</span><span class="sxs-lookup"><span data-stu-id="ff25c-564">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="ff25c-565">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff25c-565">See also</span></span>

- [<span data-ttu-id="ff25c-566">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ff25c-566">ADO.NET Overview</span></span>](ado-net-overview.md)
