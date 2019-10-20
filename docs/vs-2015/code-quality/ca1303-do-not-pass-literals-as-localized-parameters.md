---
title: 'CA1303: non passare valori letterali come parametri localizzati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661455"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Non passare valori letterali come parametri localizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft. globalizzazione|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo passa un valore letterale stringa come parametro a un costruttore o a un metodo nella libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] e tale stringa deve essere localizzabile.

 Questo avviso viene generato quando una stringa letterale viene passata come valore a un parametro o a una proprietà e uno o più dei seguenti casi è true:

- L'attributo <xref:System.ComponentModel.LocalizableAttribute> del parametro o della proprietà è impostato su true.

- Il nome del parametro o della proprietà contiene "Text", "message" o "Caption".

- Il nome del parametro stringa passato a un metodo Console. Write o console. WriteLine può essere "value" o "Format".

## <a name="rule-description"></a>Descrizione della regola
 I valori letterali stringa incorporati nel codice sorgente sono difficili da localizzare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il valore letterale stringa con una stringa recuperata tramite un'istanza della classe <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la libreria di codice non verrà localizzata o se la stringa non è esposta all'utente finale o a uno sviluppatore che usa la libreria di codice.

 Gli utenti possono eliminare il rumore da metodi a cui non devono essere passate stringhe localizzate rinominando il parametro o la proprietà denominata oppure contrassegnando questi elementi come condizionale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che genera un'eccezione quando uno dei due argomenti non è compreso nell'intervallo. Per il primo argomento, al costruttore di eccezione viene passata una stringa letterale che viola questa regola. Per il secondo argomento, al costruttore viene passata correttamente una stringa recuperata tramite un <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Risorse nelle applicazioni desktop](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
