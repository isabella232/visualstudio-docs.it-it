---
title: Proprietà degli elementi Decorator
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14965f829530ba5a2f6a7797291e9d1cfab0ae2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810054"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
Gli elementi Decorator sono icone, testo o frecce di espansione/compressione che possono essere visualizzate su forme o connettori nel diagramma. Nelle tabelle seguenti sono illustrate le proprietà dei tre tipi di elemento Decorator. Alcune delle proprietà vengono visualizzate solo negli elementi Decorator di forma o solo negli elementi Decorator del connettore.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Espandi/Comprimi elemento Decorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DisplayName|Nome dell'elemento Decorator che verrà visualizzato nella finestra di progettazione generata.|Espandi elemento Decorator compresso|
|nome|Nome dell'elemento Decorator.|ExpandCollapseDecorator|
|Note|Note informali associate a questo elemento Decorator.|\<none>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Elemento Decorator icona

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultIcon|Percorso dell'icona o del file di immagine da visualizzare.|\<none>|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Elemento Decorator icona|
|nome|Nome dell'elemento Decorator.|IconDecorator|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultText|Testo predefinito da visualizzare.|Etichetta|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Etichetta|
|FontSize|Dimensioni del carattere per il testo visualizzato nell'elemento Decorator.|8|
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Normale|
|nome|Nome dell'elemento Decorator.|Etichetta|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))