---
title: 'CA2100: esaminare le query SQL per le vulnerabilità di sicurezza | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521212"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Controllare la vulnerabilità della sicurezza nelle query SQL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Category|Microsoft.Security|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo imposta la <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> proprietà utilizzando una stringa compilata da un argomento stringa nel metodo.

## <a name="rule-description"></a>Descrizione della regola
 La regola presuppone che l'argomento stringa contenga l'input dell'utente. Una stringa di comando SQL compilata da un input dell'utente è vulnerabile agli attacchi intrusivi nel codice SQL, In un attacco SQL injection, un utente malintenzionato fornisce un input che modifica la progettazione di una query in un tentativo di danneggiare o ottenere accesso non autorizzato al database sottostante. Le tecniche tipiche includono l'inserimento di una virgoletta singola o di un apostrofo, ovvero il delimitatore di stringa letterale SQL; due trattini, che indica un commento SQL; e un punto e virgola, che indica che segue un nuovo comando. Se l'input dell'utente deve far parte della query, usare uno dei seguenti elementi, elencati in ordine di efficacia, per ridurre il rischio di attacco.

- Utilizza una stored procedure.

- Usare una stringa di comando con parametri.

- Convalidare l'input dell'utente per il tipo e il contenuto prima di compilare la stringa di comando.

  I [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] tipi seguenti implementano la <xref:System.Data.IDbCommand.CommandText%2A> proprietà o forniscono costruttori che impostano la proprietà tramite un argomento di stringa.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> e <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> e <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> e <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. Data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) e [System. Data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> e <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Si noti che questa regola viene violata quando il metodo ToString di un tipo viene usato in modo esplicito o implicito per costruire la stringa di query. Di seguito è riportato un esempio.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 La regola viene violata perché un utente malintenzionato può eseguire l'override del metodo ToString ().

 La regola viene violata anche quando si usa il metodo ToString in modo implicito.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, utilizzare una query con parametri.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il testo del comando non contiene alcun input dell'utente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `UnsafeQuery` , che viola la regola e un metodo, `SaferQuery` , che soddisfa la regola utilizzando una stringa di comando con parametri.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Panoramica della sicurezza](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
