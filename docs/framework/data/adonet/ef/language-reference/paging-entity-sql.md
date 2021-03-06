---
title: 페이징(Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 7c0a426a80db6eac6b8fdd651a7df7a9d16f577c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148719"
---
# <a name="paging-entity-sql"></a>페이징(Entity SQL)
사용 하 여 물리적 페이징을 수행할 수 있습니다는 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 및 [제한](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) 하위 절은 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 절. 결정적인 방법으로 물리적 페이징을 수행하려면 SKIP과 LIMIT를 사용해야 합니다. 비 결정적인 방식으로 결과의 행 수를 제한 하려는 경우 사용 해야 [위쪽](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)합니다. TOP과 SKIP/LIMIT는 함께 사용할 수 없습니다.  
  
## <a name="top-overview"></a>TOP 개요  
 SELECT 절에는 선택적인 TOP 하위 절과 선택적인 ALL/DISTINCT 한정자를 차례로 사용할 수 있습니다. TOP 하위 절은 쿼리 결과에 첫 번째 행 집합만 반환되도록 지정합니다. 자세한 내용은 [위쪽](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)합니다.  
  
## <a name="skip-and-limit-overview"></a>SKIP 및 LIMIT 개요  
 SKIP과 LIMIT는 ORDER BY 절의 일부입니다. SKIP 식 하위 절이 ORDER BY 절에 있으면 결과는 정렬 기준에 따라 정렬되고 SKIP 식 바로 뒤에 있는 행에서 시작하는 행이 결과 집합에 포함됩니다. 예를 들어, SKIP 5를 사용하면 처음 다섯 개의 행을 건너뛰고 여섯 번째 행부터 반환됩니다. LIMIT 식 하위 절이 ORDER BY 절에 있으면 쿼리는 정렬 지정에 따라 정렬되고 결과 행의 수는 LIMIT 식으로 제한됩니다. 예를 들어, LIMIT 5는 결과 집합을 다섯 개의 인스턴스 또는 행으로 제한합니다. SKIP과 LIMIT를 반드시 함께 사용해야 하는 것은 아니므로 ORDER BY 절에 SKIP과 LIMIT 중 하나만 사용할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>참고 항목  
 [엔터티 SQL 참조](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL 개요](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [어떻게: 쿼리 결과 페이징](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
