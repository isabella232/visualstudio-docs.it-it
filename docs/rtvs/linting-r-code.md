---
title: Lint del codice R
description: Come usare il supporto di lint predefinito per R di Visual Studio, incluse le opzioni del linter.
ms.date: 07/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 6ec955d6c105c1381d7f576a80b136eb3a54adff
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114680151"
---
# <a name="lint-r-code-in-visual-studio"></a>Lint del codice R in Visual Studio

Il linter analizza il codice per individuare potenziali errori, problemi di formattazione e altri elementi superflui nel codice, come spazi vuoti spuri. Il linter consente anche di promuovere determinate convenzioni di codifica, ad esempio la modalità di denominazione degli identificatori. Tali convenzioni sono utili nei team e in altre situazioni di collaborazione.

R Tools per Visual Studio (RTVS) offre un linter predefinito per R, con un comportamento controllabile tramite un'ampia gamma di opzioni descritte in questo articolo. Queste opzioni sono disponibili in **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **R**  >  **Lint**.

Il lint è disabilitato per impostazione predefinita. Per abilitare lint, impostare **l'opzione All**  >  **Enable lint** su **True**.

Dopo l'abilitazione, il linter viene eseguito nell'editor durante la digitazione. I problemi vengono segnalati tramite sottolineature ondulate verdi. Nella figura seguente, ad esempio, RTVS ha identificato sei problemi di lint, tra i quali l'uso di `=` invece di `<-` per un'assegnazione, la mancanza di spazio attorno agli argomenti della funzione, l'uso di identificatori con la notazione Pascal e con tutte maiuscole e l'uso di un punto e virgola. Posizionando il puntatore del mouse su un problema viene visualizzata una descrizione.

![Esempi di output del linter per il codice R](media/linting-01.png)

È spesso necessario modificare le opzioni del linter a seconda delle esigenze di un progetto o un file. Ad esempio, il codice di esempio da un corso online potrebbe usare `=` invece di `<-` insieme agli identificatori con convenzione per le maiuscole/minuscole Pascal. Per questo codice verrebbero visualizzati avvisi del linter frequenti, perché le opzioni del linter predefinite contrassegnano questa convenzione per le maiuscole/minuscole. Durante l'utilizzo di tale codice è quindi possibile disabilitare le opzioni anziché dedicare tempo a correggere ogni istanza.

## <a name="assignment-group"></a>Gruppo Assegnazione

| Opzione | Valore predefinito | Effetto di lint |
| --- | --- | --- |
| **rinforzare \<-** | **True** | Identifica quando `<-` non viene usato per un'assegnazione. |

## <a name="naming-group"></a>Gruppo Denominazione

Queste opzioni consentono di contrassegnare gli identificatori che usano convenzioni di denominazione diverse:

| Opzione | Valore predefinito | Effetto di lint |
| --- | --- | --- |
| **Contrassegna camelCase** | **False** | Contrassegna gli identificatori che usano la notazione Camel. |
| **Contrassegna nomi lunghi** | **False** | Contrassegna gli identificatori con un nome con una lunghezza superiore all'impostazione **Lunghezza massima del nome**. |
| **Contrassegna più punti** | **True** | Contrassegna gli identificatori che usano più punti. |
| **Contrassegna PascalCase** | **True** | Contrassegna gli identificatori che usano la notazione Pascal. |
| **Contrassegna snake_case** | **False** | Contrassegna gli identificatori che usano caratteri di sottolineatura. |
| **Contrassegna MAIUSCOLE** | **True** | Contrassegna gli identificatori che usano tutte maiuscole. |
| **Lunghezza massima del nome** | **32** | La lunghezza applicata con l'impostazione **Contrassegna nomi lunghi**. |

## <a name="spacing-group"></a>Gruppo Spaziatura

Queste opzioni, impostate tutte su **True** per impostazione predefinita, determinano la posizione in cui il linter identifica i problemi di spaziatura: dopo i nomi di funzione, tra le virgole, tra gli operatori, le posizioni delle parentesi graffe aperte e chiuse, lo spazio prima di ( e lo spazio all'interno di ().

## <a name="statements-group"></a>Gruppo Istruzioni

| Opzione | Valore predefinito | Effetto di lint |
| --- | --- | --- |
| **Più di uno** | **True** | Identifica se più istruzioni sono sulla stessa riga. |
| **Punti e virgola** | **True** | Identifica l'uso di punti e virgola. |

## <a name="text-group"></a>Gruppo Testo

| Opzione | Valore predefinito | Effetto di lint |
| --- | --- | --- |
| **Limite di lunghezza della riga** | **False** | Imposta un valore che indica se l'intervallo contrassegna le righe più lunghe rispetto **all'opzione Lunghezza massima** riga. |
| **Lunghezza massima della riga** | **80** | Imposta la lunghezza della linea applicata **dall'opzione Limite lunghezza** riga. |

## <a name="whitespace-group"></a>Gruppo Spazio vuoto

Queste opzioni, impostate tutte su **True** per impostazione predefinita, determinano la posizione in cui il linter identifica i problemi di spazio vuoto: uso delle schede, uso di virgolette doppie, righe vuote finali e spazi vuoti finali.