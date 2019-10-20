---
title: Proprietà delle corsie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b76bef291e23bc570534aa79f9471453c59491c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671333"
---
# <a name="properties-of-swimlanes"></a>Proprietà delle corsie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere corsie a un diagramma. Le corsie dividono un diagramma in aree verticali o orizzontali. È possibile definire altre forme da visualizzare all'interno delle corsie. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le corsie hanno le proprietà elencate nella tabella seguente.

|proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Colore riempimento corpo|Colore di riempimento per il corpo della corsia.|bianco|
|Colore riempimento intestazione|Colore di riempimento per l'intestazione della corsia.|DarkGray|
|Colore separatore|Colore della linea di separazione.|LightGray|
|Stile linea separatore|Stile della linea di separazione (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` o `Custom`).|`Dash`|
|Spessore separatore|Spessore in pollici della linea del separatore.|0,03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator di testo associati a questa corsia.|Nero|
|Modificatore di accesso|Livello di accesso della classe (`public` o `internal`).|Public|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice generata da questa corsia.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla corsia (`none`, `abstract` o `sealed`).|none|
|Corsia di base|Classe di base di questa corsia.|(nessuno)|
|Name|Nome di questa corsia.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi affiliato a questa corsia.|Spazio dei nomi corrente|
|Tipo di descrizione comando|Modalità di definizione della descrizione comando (`fixed`, `variable` o `none`). Se `fixed`, viene usato il valore della proprietà `Fixed Tooltip Text`. Se `variable`, la descrizione comando è definita nel codice personalizzato.|\<nessuno>|
|Note|Note informali associate a questa corsia.|\<nessuno>|
|Allineamento|Allineamento orizzontale o verticale.|Vertical|
|Altezza iniziale|Altezza iniziale della corsia, in pollici. Applicabile solo alle corsie orizzontali.|0|
|Larghezza iniziale|Larghezza iniziale della corsia, in pollici. Applicabile solo alle corsie verticali.|0|
|Espone il colore del testo|Se `True`, l'utente può impostare il colore di una corsia nella finestra di progettazione generata. Per impostare questa impostazione, fare clic con il pulsante destro del mouse sulla forma corsia e scegliere **Aggiungi esposti**.|False|
|Descrizione|Utilizzato per documentare la finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per fare riferimento a questa classe di corsia.|\<nessuno>|
|Testo della descrizione comando fisso|Testo utilizzato per una descrizione comando fissa.|\<nessuno>|
|Parola chiave della Guida|Parola chiave utilizzata per indicizzare la Guida sensibile al contesto per questa corsia.|\<nessuno>|

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
