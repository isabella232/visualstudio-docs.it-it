---
title: 'CA1801: rivedere i parametri inutilizzati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: caf1ec865d604545940b0a5442947ef61bd60f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671536"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Rivedere i parametri inutilizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1801: rivedere i parametri inutilizzati](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Category|Microsoft. Usage|
|Modifica importante|Senza interruzioni: se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br /><br /> Senza interruzioni: se si modifica il membro per usare il parametro all'interno del corpo.<br /><br /> Suddivisione: se si rimuove il parametro ed è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Una firma di metodo include un parametro non utilizzato nel corpo del metodo. Questa regola non esamina i metodi seguenti:

- Metodi a cui fa riferimento un delegato.

- Metodi utilizzati come gestori eventi.

- Metodi dichiarati con il modificatore `abstract` (`MustOverride` nel Visual Basic).

- Metodi dichiarati con il modificatore `virtual` (`Overridable` nel Visual Basic).

- Metodi dichiarati con il modificatore `override` (`Overrides` nel Visual Basic).

- Metodi dichiarati con il modificatore `extern` (`Declare` istruzione nel Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Esaminare i parametri nei metodi non virtuali che non vengono utilizzati nel corpo del metodo per assicurarsi che non esista alcuna correttezza in caso di errore di accesso. I parametri inutilizzati comportano costi di manutenzione e di prestazioni.

 Talvolta una violazione di questa regola può puntare a un bug di implementazione nel metodo. Ad esempio, il parametro deve essere stato usato nel corpo del metodo. Non visualizzare gli avvisi di questa regola se il parametro deve esistere a causa della compatibilità con le versioni precedenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il parametro inutilizzato (una modifica di rilievo) o utilizzare il parametro nel corpo del metodo, ovvero una modifica senza interruzioni.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola per il codice distribuito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due metodi. Un metodo viola la regola e l'altro metodo soddisfa la regola.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)
