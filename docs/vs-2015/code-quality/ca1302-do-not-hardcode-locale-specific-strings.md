---
title: 'CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 23f2b807d66662691afaa4805a50b34255a39bdb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842417"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo utilizza un valore letterale stringa che rappresenta una parte del percorso di determinate cartelle di sistema.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumerazione contiene i membri che fanno riferimento a cartelle di sistema speciali. I percorsi di queste cartelle possono avere valori diversi nei sistemi operativi diversi, l'utente può modificare alcune delle posizioni e i percorsi sono localizzati. Un esempio di una cartella speciale è la cartella di sistema, ovvero "C:\WINDOWS\system32" nella [!INCLUDE[winxp](../includes/winxp-md.md)] ma "C:\Winnt\System32." su [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. Il <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> metodo restituisce i percorsi che sono associati le <xref:System.Environment.SpecialFolder> enumerazione. I percorsi restituiti da <xref:System.Environment.GetFolderPath%2A> sono localizzati e appropriati per il computer in uso.

 Questa regola suddivide in token i percorsi delle cartelle che vengono recuperati utilizzando la <xref:System.Environment.GetFolderPath%2A> metodo in livelli di directory separate. Ogni valore letterale stringa viene confrontato con i token. Se viene trovata una corrispondenza, si presuppone che il metodo sta creando una stringa che rappresenta il percorso di sistema che è associato il token. Per la portabilità e la verifica della localizzabilità, usare il <xref:System.Environment.GetFolderPath%2A> metodo per recuperare i percorsi delle cartelle di sistema speciale invece di usare valori letterali stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, recuperare il percorso utilizzando la <xref:System.Environment.GetFolderPath%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il valore letterale stringa non viene utilizzata per fare riferimento a uno dei percorsi di sistema che è associato il <xref:System.Environment.SpecialFolder> enumerazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente compila il percorso della cartella dati applicazioni comuni che genera tre avvisi da questa regola. Successivamente, l'esempio recupera il percorso utilizzando la <xref:System.Environment.GetFolderPath%2A> (metodo).

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)



