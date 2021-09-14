---
title: Proprietà degli elementi Decorator
description: Si apprenderà che gli elementi Decorator sono icone, testo o caselle di espansione/compressione che possono essere visualizzate in forme o connettori nel diagramma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: bfbec75b8190b56900a7a994ac12022af1133ac0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637580"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
Gli elementi Decorator sono icone, testo o espansione/compressione che possono essere visualizzati in forme o connettori nel diagramma. Nelle tabelle seguenti vengono mostrate le proprietà per i tre tipi di elemento Decorator. Alcune delle proprietà vengono visualizzate solo sugli elementi Decorator della forma o solo sugli elementi Decorator del connettore.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione [di un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

## <a name="expandcollapse-decorator"></a>Espandi/Comprimi elemento Decorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DisplayName|Nome dell'elemento Decorator che verrà visualizzato nella finestra di progettazione generata.|Espandere Comprimi elemento Decorator|
|Nome|Nome dell'elemento Decorator.|Expandcollapsedecorator|
|Note|Note informali associate a questo elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|Verticaloffset|Offset verticale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Elemento Decorator icona

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultIcon|Percorso dell'icona o del file di immagine da visualizzare.|\<none>|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Elemento Decorator icona|
|Nome|Nome dell'elemento Decorator.|IconDecorator|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|Verticaloffset|Offset verticale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>Textdecorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultText|Testo predefinito da visualizzare.|Label|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Label|
|FontSize|Dimensione del carattere per il testo visualizzato nell'elemento Decorator.|8|
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Normale|
|Nome|Nome dell'elemento Decorator.|Label|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|Verticaloffset|Offset verticale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))