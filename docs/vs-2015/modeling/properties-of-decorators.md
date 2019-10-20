---
title: Proprietà degli elementi Decorator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652011"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli elementi Decorator sono icone, testo o frecce di espansione/compressione che possono essere visualizzate su forme o connettori nel diagramma. Nelle tabelle seguenti sono illustrate le proprietà dei tre tipi di elemento Decorator. Alcune delle proprietà vengono visualizzate solo negli elementi Decorator di forma o solo negli elementi Decorator del connettore.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Espandi/Comprimi elemento Decorator

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|DisplayName|Nome dell'elemento Decorator che verrà visualizzato nella finestra di progettazione generata.|Espandi elemento Decorator compresso|
|Name|Nome dell'elemento Decorator.|ExpandCollapseDecorator|
|Note|Note informali associate a questo elemento Decorator.|\<nessuno>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Elemento Decorator icona

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|DefaultIcon|Percorso dell'icona o del file di immagine da visualizzare.|\<nessuno>|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Elemento Decorator icona|
|Name|Nome dell'elemento Decorator.|IconDecorator|
|Note|Note informali associate all'elemento Decorator.|\<nessuno>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|DefaultText|Testo predefinito da visualizzare.|Label|
|DisplayName|Nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata.|Label|
|FontSize|Dimensioni del carattere per il testo visualizzato nell'elemento Decorator.|8|
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Regular|
|Name|Nome dell'elemento Decorator.|Label|
|Note|Note informali associate all'elemento Decorator.|\<nessuno>|
|HorizontalOffset|Offset orizzontale, in pollici, relativo alla posizione predefinita dell'elemento Decorator. (Solo su forme).|0|
|VerticalOffset|Offset verticale rispetto alla posizione predefinita dell'elemento Decorator, in pollici. (Solo su forme).|0|
|OffsetFromLine|Offset dell'elemento Decorator dalla riga rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|OffsetFromShape|Offset dell'elemento Decorator dalla forma rispetto alla posizione predefinita, in pollici. (Solo sui connettori).|0|
|Posizione|Posizione predefinita dell'elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
