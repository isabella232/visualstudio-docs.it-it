---
title: 'CA1702: le parole composte devono essere corrette correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f9dc15cec4012d2b63eb5f21c25bd709961c95c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544079"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [CA1702: le parole composte devono essere configurate correttamente](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|Elemento|valore|
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Category|Microsoft. Naming|
|Modifica importante|Interruzioni durante l'attivazione degli assembly.<br /><br /> Senza interruzioni: quando viene attivato sui parametri di tipo.|

## <a name="cause"></a>Causa
 Il nome di un identificatore contiene più parole e almeno una delle parole sembra essere una parola composta non corretta.

## <a name="rule-description"></a>Descrizione della regola
 Il nome dell'identificatore viene suddiviso in parole basate sulla combinazione di maiuscole e minuscole. Ogni combinazione di due parole contigue viene controllata dalla libreria del correttore ortografico Microsoft. Se viene riconosciuta, l'identificatore produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", che devono essere considerati come "checksum" e "multipart", rispettivamente. A causa dell'utilizzo comune precedente, vengono compilate diverse eccezioni nella regola e vengono contrassegnate diverse parole, ad esempio "barra degli strumenti" e "nomefile", che devono essere racchiuse tra due parole distinte, in questo caso "barra degli strumenti" e "nomefile".

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che sia inserito correttamente nel caso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografico e l'intento è usare due parole.

## <a name="related-rules"></a>Regole correlate
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) per la denominazione delle [convenzioni di capitalizzazione](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
