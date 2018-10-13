---
title: Proprietà degli elementi Decorator | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2d7d6aec514cab53777840730dee6bafac51512e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276887"
---
# <a name="properties-of-decorators"></a>Proprietà degli elementi Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli elementi Decorator sono icone, testo o parentesi angolari di espansione/compressione che è possono visualizzare forme o connettori nel diagramma. Le tabelle seguenti illustrano le proprietà per i tre tipi di elemento decorator. Alcune delle proprietà vengono visualizzate solo in shape-elementi Decorator o solo su decoratori del connettore.  
  
 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Espandi/Comprimi elemento Decorator  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|DisplayName|Il nome dell'elemento decorator che verrà visualizzato nella finestra di progettazione generata.|Espandere Comprimi elemento Decorator|  
|nome|Il nome dell'elemento decorator.|ExpandCollapseDecorator|  
|Note|Note informali associate a questo elemento decorator.|\<Nessuno >|  
|HorizontalOffset|Offset orizzontale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|VerticalOffset|L'offset verticale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|OffsetFromLine|L'offset dell'elemento decorator dalla linea, rispetto alla relativa posizione predefinita, in pollici. (Su connettori solo.)|0|  
|OffsetFromShape|L'offset dell'elemento decorator dalla forma, rispetto alla posizione predefinita, in pollici. (Su connettori solo.)|0|  
|Posizione|La posizione predefinita dell'elemento decorator.|SourceTop|  
  
## <a name="icon-decorator"></a>Elemento Decorator di icona  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|DefaultIcon|Il percorso del file icona o un'immagine da visualizzare.|\<Nessuno >|  
|DisplayName|Il nome dell'elemento decorator da visualizzare nella finestra di progettazione generata.|Elemento Decorator di icona|  
|nome|Il nome dell'elemento decorator.|IconDecorator|  
|Note|Note informali associate con l'elemento decorator.|\<Nessuno >|  
|HorizontalOffset|Offset orizzontale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|VerticalOffset|L'offset verticale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|OffsetFromLine|L'offset dell'elemento decorator dalla linea, rispetto alla relativa posizione predefinita, in pollici. (Su connettori solo.)|0|  
|OffsetFromShape|L'offset dell'elemento decorator dalla forma, rispetto alla posizione predefinita, in pollici. (Su connettori solo.)|0|  
|Posizione|La posizione predefinita dell'elemento decorator.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|DefaultText|Il testo predefinito da visualizzare.|Label|  
|DisplayName|Il nome dell'elemento decorator da visualizzare nella finestra di progettazione generata.|Label|  
|FontSize|Le dimensioni del carattere per il testo visualizzato nell'elemento decorator.|8|  
|FontStyle|Lo stile del carattere per il testo visualizzato nell'elemento decorator.|Regular|  
|nome|Il nome dell'elemento decorator.|Label|  
|Note|Note informali associate con l'elemento decorator.|\<Nessuno >|  
|HorizontalOffset|Offset orizzontale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|VerticalOffset|L'offset verticale rispetto alla posizione predefinita dell'elemento decorator, espresso in pollici. (Sulle forme solo.)|0|  
|OffsetFromLine|L'offset dell'elemento decorator dalla linea, rispetto alla relativa posizione predefinita, in pollici. (Su connettori solo.)|0|  
|OffsetFromShape|L'offset dell'elemento decorator dalla forma, rispetto alla posizione predefinita, in pollici. (Su connettori solo.)|0|  
|Posizione|La posizione predefinita dell'elemento decorator.|TargetBottom|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



