---
title: Proprietà degli elementi Decorator
description: Si apprenderà che gli elementi Decorator sono icone, testo o scacchiere di espansione/compressione che possono essere visualizzati su forme o connettori nel diagramma.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034201"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
Gli elementi Decorator sono icone, testo o scacchiere di espansione/compressione che possono essere visualizzati su forme o connettori nel diagramma. Le tabelle seguenti illustrano le proprietà per i tre tipi di elemento Decorator. Alcune delle proprietà vengono visualizzate solo sugli elementi Decorator della forma o solo sugli elementi Decorator del connettore.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Elemento Decorator espandi/comprimi

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DisplayName|Nome dell'elemento Decorator che verrà visualizzato nella finestra di progettazione generata.|Espandere Comprimi elemento Decorator|
|Nome|Nome dell'elemento Decorator.|Expandcollapsedecorator|
|Note|Note informali associate a questo elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|Verticaloffset|Offset verticale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Elemento Decorator icona

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultIcon|Percorso dell'icona o del file di immagine da visualizzare.|\<none>|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Elemento Decorator icona|
|Nome|Nome dell'elemento Decorator.|IconaDecorator|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|Verticaloffset|Offset verticale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>Textdecorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultText|Testo predefinito da visualizzare.|Etichetta|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Etichetta|
|FontSize|Dimensione del carattere per il testo visualizzato nell'elemento Decorator.|8|
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Normale|
|Nome|Nome dell'elemento Decorator.|Etichetta|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|Horizontaloffset|Offset orizzontale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|Verticaloffset|Offset verticale, relativo alla posizione predefinita dell'elemento Decorator, in pollici. (Solo per le forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, in pollici. (Solo per i connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))