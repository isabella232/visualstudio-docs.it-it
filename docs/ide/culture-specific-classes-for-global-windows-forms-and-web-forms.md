---
title: Classi specifiche delle impostazioni cultura per Windows Form e Web Form globali
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c311e9c79e4f2861b8b52852ff7bb9b0217bf22c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948037"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Classi specifiche delle impostazioni cultura per Windows Form e Web Form globali

Le impostazioni cultura hanno diverse convenzioni per la visualizzazione di date, ore, numeri, valute e altre informazioni. Lo spazio dei nomi <xref:System.Globalization> contiene classi che possono essere usate per modificare il modo in cui i valori specifici delle impostazioni cultura vengono visualizzati, ad esempio:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendario**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Uso delle impostazioni cultura

Usare le impostazioni cultura, archiviate nell'applicazione o nel pannello di controllo **Opzioni internazionali**, per determinare le convenzioni culturali in fase di runtime e formattare le informazioni di conseguenza. Per altre informazioni sulla definizione delle impostazioni cultura, vedere [Procedura: Impostare le impostazioni cultura e le impostazioni cultura dell'interfaccia utente per la globalizzazione della pagina Web ASP.NET](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Le classi che formattano automaticamente le informazioni in base alle impostazioni cultura sono denominate *specifiche delle impostazioni cultura*. Alcuni metodi specifici delle impostazioni cultura sono
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Alcune funzioni specifiche delle impostazioni cultura (nel linguaggio Visual Basic) sono `MonthName` e `WeekDayName`.

Ad esempio, il codice seguente illustra come poter usare il metodo <xref:System.IFormattable.ToString%2A> per la formattazione della valuta per le impostazioni cultura correnti:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Se le impostazioni cultura sono impostate su "fr-FR", nella finestra di output verrà visualizzato quanto segue:

`100,00`

Se le impostazioni cultura sono impostate su "en-US", nella finestra di output verrà visualizzato quanto segue:

`$100.00`

## <a name="see-also"></a>Vedere anche

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)