---
title: 'CA1306: Specificare le impostazioni locali per i tipi di dati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9a7188f3679e04164411472fd2d53948466a30d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Specificare le impostazioni locali per i tipi di dati
|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo o costruttore creato uno o più <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> istanze e non imposta in modo esplicito le proprietà delle impostazioni locali (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Descrizione della regola
 Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e criterio di ordinamento. Quando si crea un <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, è necessario impostare in modo esplicito le impostazioni locali. Per impostazione predefinita, le impostazioni locali per questi tipi sono le impostazioni cultura correnti. Per i dati vengono archiviati in un database o i file e vengono condivise globalmente, in genere il locale deve essere impostato per la lingua inglese (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Quando i dati vengono condivisi tra più impostazioni cultura, utilizzando le impostazioni locali predefinite può causare il contenuto del <xref:System.Data.DataTable> o <xref:System.Data.DataSet> la presentazione o interpretato in modo non corretto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare in modo esplicito le impostazioni locali per il <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la raccolta o l'applicazione è per un pubblico locale limitato, i dati non sono condivisa o l'impostazione predefinita produce il comportamento desiderato in tutti gli scenari supportati.

## <a name="example"></a>Esempio
 L'esempio seguente crea due <xref:System.Data.DataTable> istanze.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> <xref:System.Globalization.CultureInfo?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>