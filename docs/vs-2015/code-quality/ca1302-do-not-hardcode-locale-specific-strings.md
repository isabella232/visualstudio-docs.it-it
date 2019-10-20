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
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661481"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo usa un valore letterale stringa che rappresenta parte del percorso di alcune cartelle di sistema.

## <a name="rule-description"></a>Descrizione della regola
 L'enumerazione <xref:System.Environment.SpecialFolder?displayProperty=fullName> contiene membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono avere valori diversi in sistemi operativi diversi, l'utente può modificare alcuni percorsi e i percorsi sono localizzati. Un esempio di cartella speciale è la cartella di sistema, ovvero "C:\WINDOWS\system32" in [!INCLUDE[winxp](../includes/winxp-md.md)] ma "C:\WINNT\system32" su [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. Il metodo <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> restituisce i percorsi associati all'enumerazione <xref:System.Environment.SpecialFolder>. I percorsi restituiti da <xref:System.Environment.GetFolderPath%2A> sono localizzati e appropriati per il computer attualmente in esecuzione.

 Questa regola suddivide in token i percorsi di cartella recuperati usando il metodo <xref:System.Environment.GetFolderPath%2A> in livelli di directory distinti. Ogni valore letterale stringa viene confrontato con i token. Se viene trovata una corrispondenza, si presuppone che il metodo stia compilando una stringa che fa riferimento al percorso di sistema associato al token. Per la portabilità e la localizzabilità, utilizzare il metodo <xref:System.Environment.GetFolderPath%2A> per recuperare i percorsi delle cartelle di sistema speciali anziché utilizzare valori letterali stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, recuperare il percorso usando il metodo <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il valore letterale stringa non viene usato per fare riferimento a uno dei percorsi di sistema associati all'enumerazione <xref:System.Environment.SpecialFolder>.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene compilato il percorso della cartella Common Application Data, che genera tre avvisi da questa regola. Successivamente, l'esempio recupera il percorso usando il metodo <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
