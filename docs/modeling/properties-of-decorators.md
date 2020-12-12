---
title: Proprietà degli elementi Decorator
description: Informazioni sugli elementi Decorator sono icone, testo o espansione/compressione di frecce che possono essere visualizzate su forme o connettori nel diagramma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef863d0d3dab394c2ca427a27d039c19e5921a51
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360833"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
Gli elementi Decorator sono icone, testo o frecce di espansione/compressione che possono essere visualizzate su forme o connettori nel diagramma. Nelle tabelle seguenti sono illustrate le proprietà dei tre tipi di elemento Decorator. Alcune delle proprietà vengono visualizzate solo negli elementi Decorator di forma o solo negli elementi Decorator del connettore.

 Per ulteriori informazioni, vedere [come definire un linguaggio Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Espandi/Comprimi elemento Decorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DisplayName|Nome dell'elemento Decorator che verrà visualizzato nella finestra di progettazione generata.|Espandi elemento Decorator compresso|
|Nome|Nome dell'elemento Decorator.|ExpandCollapseDecorator|
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
|Nome|Nome dell'elemento Decorator.|IconDecorator|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|DefaultText|Testo predefinito da visualizzare.|Label|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Label|
|FontSize|Dimensioni del carattere per il testo visualizzato nell'elemento Decorator.|8|
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Regular|
|Nome|Nome dell'elemento Decorator.|Label|
|Note|Note informali associate all'elemento Decorator.|\<none>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))