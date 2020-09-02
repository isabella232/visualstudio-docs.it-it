---
title: 'CA1302: non impostare come hardcoded le stringhe delle impostazioni locali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539009"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo usa un valore letterale stringa che rappresenta parte del percorso di alcune cartelle di sistema.

## <a name="rule-description"></a>Descrizione della regola
 L' <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumerazione contiene membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono avere valori diversi in sistemi operativi diversi, l'utente può modificare alcuni percorsi e i percorsi sono localizzati. Un esempio di cartella speciale è la cartella di sistema, ovvero "C:\WINDOWS\system32" in, [!INCLUDE[winxp](../includes/winxp-md.md)] ma "C:\Winnt\System32" in [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . Il <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> metodo restituisce le posizioni associate all' <xref:System.Environment.SpecialFolder> enumerazione. I percorsi restituiti da <xref:System.Environment.GetFolderPath%2A> sono localizzati e appropriati per il computer attualmente in esecuzione.

 Questa regola suddivide in token i percorsi di cartella recuperati usando il <xref:System.Environment.GetFolderPath%2A> metodo in livelli di directory distinti. Ogni valore letterale stringa viene confrontato con i token. Se viene trovata una corrispondenza, si presuppone che il metodo stia compilando una stringa che fa riferimento al percorso di sistema associato al token. Per la portabilità e la localizzabilità, utilizzare il <xref:System.Environment.GetFolderPath%2A> metodo per recuperare i percorsi delle cartelle di sistema speciali anziché utilizzare valori letterali stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, recuperare il percorso usando il <xref:System.Environment.GetFolderPath%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il valore letterale stringa non viene usato per fare riferimento a uno dei percorsi di sistema associati all' <xref:System.Environment.SpecialFolder> enumerazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene compilato il percorso della cartella Common Application Data, che genera tre avvisi da questa regola. Successivamente, l'esempio recupera il percorso usando il <xref:System.Environment.GetFolderPath%2A> metodo.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
