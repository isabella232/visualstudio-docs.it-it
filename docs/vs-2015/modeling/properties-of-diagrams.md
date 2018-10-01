---
title: Proprietà di diagrammi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 43d5804f1a80b2616e209c47e594b29ad84911a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527006"
---
# <a name="properties-of-diagrams"></a>Proprietà di diagrammi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [delle proprietà di diagrammi](https://docs.microsoft.com/visualstudio/modeling/properties-of-diagrams).  
  
È possibile impostare le proprietà che specificano come diagrammi apparirà nella finestra di progettazione generata. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.  
  
 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Nella tabella seguente sono elencate le proprietà dei diagrammi.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore riempimento|Il colore di riempimento per il diagramma.|Bianco|  
|Colore del testo|Colore del testo che viene visualizzato nel diagramma.|Nero|  
|Modificatore di accesso|Il modificatore di accesso della classe (pubblico o interno).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe del codice generato.|\<Nessuno >|  
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dal diagramma (`none`, `abstract` o `sealed`).|nessuno|  
|Diagramma di base|Classe di base di questo diagramma.|(nessuno)|  
|nome|Il nome di questo diagramma.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è associato a questo diagramma.|Spazio dei nomi corrente|  
|Classe rappresentata|La classe di dominio radice che rappresenta questo diagramma.|Classe radice corrente se applicabile|  
|Note|Note informali associate a questo elemento.|\<Nessuno >|  
|Colore di riempimento esposte come proprietà|Se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata. Per procedere, fare clic con il pulsante destro della forma di diagramma e fare clic su **Explosed aggiungere**.|False|  
|Espone il colore del testo come proprietà|Se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata. Per procedere, fare clic con il pulsante destro della forma di diagramma e fare clic su **Explosed aggiungere**.|False|  
|Descrizione|La descrizione che consente di documentare la finestra di progettazione generata.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per il diagramma.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida F1 per questo diagramma.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



