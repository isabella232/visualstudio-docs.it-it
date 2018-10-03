---
title: 'CA1303: Non passare valori letterali parametri come localizzati | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fcb7f9f4cd57f287ec7a2bab900a78d21f23846
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589219"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Non passare valori letterali come parametri localizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1303: non passare valori letterali come localizzati parametri](https://docs.microsoft.com/visualstudio/code-quality/ca1303-do-not-pass-literals-as-localized-parameters).

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft.Globalization|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo passa una stringa letterale come parametro a un costruttore o un metodo nel [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] classi della libreria e questa stringa deve essere localizzabile.

 Questo avviso viene generato quando una valore letterale stringa viene passata come valore per un parametro o una proprietà e uno o più delle seguenti condizioni sono true:

-   Il <xref:System.ComponentModel.LocalizableAttribute> attributi del parametro o della proprietà sono impostato su true.

-   Il nome di parametro o una proprietà contiene "Text", "Messaggio" o "Caption".

-   Il nome del parametro di stringa che viene passato a un metodo Console. Write o console. WriteLine è "value" o "format".

## <a name="rule-description"></a>Descrizione della regola
 Valori letterali stringa incorporati nel codice sorgente sono difficili da localizzare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il valore letterale stringa con una stringa recuperata tramite un'istanza di <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la libreria di codice non verrà localizzata, o se la stringa non viene esposto all'utente finale o a uno sviluppatore che usa la libreria di codice.

 Gli utenti possono eliminare le segnalazioni con i metodi che non deve essere passato stringhe localizzate rinominando il parametro o una proprietà denominata o contrassegnando tali elementi come condizionale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che genera un'eccezione se uno dei due argomenti sono comprese nell'intervallo. Per il primo argomento, il costruttore di eccezione viene passato una stringa letterale che viola questa regola. Per il secondo argomento, il costruttore correttamente viene passato una stringa recuperata tramite una <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Risorse nelle applicazioni desktop](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



