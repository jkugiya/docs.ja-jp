---
description: '詳細情報: REF CURSOR の例'
title: REF CURSOR の例
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: e7cb411778b325400d37511b082032e590b339c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773226"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="db9b4-103">REF CURSOR の例</span><span class="sxs-lookup"><span data-stu-id="db9b4-103">REF CURSOR Examples</span></span>

<span data-ttu-id="db9b4-104">REF CURSOR の例は、REF CURSOR の使い方を説明する、次の 3 つの Microsoft Visual Basic の例によって構成されています。</span><span class="sxs-lookup"><span data-stu-id="db9b4-104">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="db9b4-105">サンプル</span><span class="sxs-lookup"><span data-stu-id="db9b4-105">Sample</span></span>|<span data-ttu-id="db9b4-106">説明</span><span class="sxs-lookup"><span data-stu-id="db9b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db9b4-107">OracleDataReader の REF CURSOR パラメーター</span><span class="sxs-lookup"><span data-stu-id="db9b4-107">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="db9b4-108">この例では、REF CURSOR パラメーターを返し、<xref:System.Data.OracleClient.OracleDataReader> として値を読み込む PL/SQL ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-108">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="db9b4-109">OracleDataReader を使用した複数の REF CURSOR からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="db9b4-109">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="db9b4-110">この例では、2 つの REF CURSOR パラメーターを返し、**OracleDataReader** を使用して値を読み込む PL/SQL ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-110">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="db9b4-111">1 つまたは複数の REF CURSOR を使用した DataSet の値の設定</span><span class="sxs-lookup"><span data-stu-id="db9b4-111">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="db9b4-112">この例では、2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する PL/SQL ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-112">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="db9b4-113">これらの例を使用するには、必要に応じて Oracle テーブルを作成し、さらに PL/SQL パッケージとパッケージ本体を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db9b4-113">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="db9b4-114">Oracle テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="db9b4-114">Creating the Oracle Tables</span></span>  

 <span data-ttu-id="db9b4-115">これらの例では、Oracle Scott/Tiger スキーマで定義されたテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-115">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="db9b4-116">Oracle Scott/Tiger スキーマは、ほとんどの Oracle のインストールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="db9b4-116">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="db9b4-117">このスキーマが含まれていない場合は、{OracleHome}\rdbms\admin\scott.sql にある SQL コマンド ファイルを使用して、これらの例で使用されているテーブルとインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-117">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="db9b4-118">Oracle パッケージとパッケージ本体の作成</span><span class="sxs-lookup"><span data-stu-id="db9b4-118">Creating the Oracle Package and Package Body</span></span>  

 <span data-ttu-id="db9b4-119">これらの例では、次の PL/SQL パッケージとパッケージ本体がサーバー上に必要になります。</span><span class="sxs-lookup"><span data-stu-id="db9b4-119">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="db9b4-120">次の Oracle パッケージを Oracle サーバー上に作成します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-120">Create the following Oracle package on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
    TYPE T_CURSOR IS REF CURSOR;
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,
                               IO_CURSOR IN OUT T_CURSOR);
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/
```  
  
 <span data-ttu-id="db9b4-121">Oracle サーバーで、次の Oracle パッケージ本体を作成します。</span><span class="sxs-lookup"><span data-stu-id="db9b4-121">Create the following Oracle package body on the Oracle server.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS
        V_CURSOR T_CURSOR;
    BEGIN
        IF N_EMPNO <> 0
        THEN  
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;
    END OPEN_ONE_CURSOR;
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS
        V_CURSOR1 T_CURSOR;
        V_CURSOR2 T_CURSOR;
    BEGIN
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;
        DEPTCURSOR := V_CURSOR2;
    END OPEN_TWO_CURSORS;
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="db9b4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="db9b4-122">See also</span></span>

- [<span data-ttu-id="db9b4-123">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="db9b4-123">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="db9b4-124">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="db9b4-124">ADO.NET Overview</span></span>](ado-net-overview.md)
