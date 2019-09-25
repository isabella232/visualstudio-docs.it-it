---
title: 'CA1306: Specificare le impostazioni locali per i tipi di dati'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf16ccd187681be7406fdadbde620a167a40c96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235019"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Specificare le impostazioni locali per i tipi di dati

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un metodo o un costruttore ha creato una <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> più istanze di o e non ha impostato in modo esplicito<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> la <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>proprietà delle impostazioni locali (o).

## <a name="rule-description"></a>Descrizione della regola
Le impostazioni locali determinano elementi di presentazione specifici delle impostazioni cultura per i dati, ad esempio la formattazione utilizzata per valori numerici, simboli di valuta e ordinamento. Quando si crea un <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, è necessario impostare le impostazioni locali in modo esplicito. Per impostazione predefinita, le impostazioni locali per questi tipi sono le impostazioni cultura correnti. Per i dati archiviati in un database o in un file e condivisi a livello globale, le impostazioni locali devono essere in genere impostate sulla lingua inglese (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Quando i dati vengono condivisi tra le diverse impostazioni cultura, l'utilizzo delle impostazioni locali predefinite può <xref:System.Data.DataTable> causare <xref:System.Data.DataSet> la presentazione o l'interpretazione non corretta del contenuto dell'oggetto o.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, impostare in modo esplicito le impostazioni locali <xref:System.Data.DataTable> per <xref:System.Data.DataSet>o.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato, i dati non vengono condivisi o l'impostazione predefinita produce il comportamento desiderato in tutti gli scenari supportati.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono create <xref:System.Data.DataTable> due istanze.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>