---
title: Panoramica dell'integrazione di controllo di origine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e2761958cd60721ccf05a14ec54d3e365572ea1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148349"
---
# <a name="source-control-integration-overview"></a>Panoramica dell'integrazione del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa sezione Confronta i due modi per integrare nel controllo del codice sorgente Visual Studio; un controllo del codice sorgente del plug-in e un pacchetto VSPackage che fornisce una soluzione di controllo del codice sorgente e vengono evidenziate le nuove funzionalità di controllo di origine. Visual Studio consente il passaggio manuale tra controllo del codice sorgente pacchetti VSPackage e plug-in controllo codice sorgente, nonché basati su soluzioni un passaggio automatico.  
  
## <a name="source-control-integration"></a>Integrazione del controllo codice sorgente  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta due tipi di opzioni di integrazione del controllo sorgente. In tutte le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è comunque possibile integrare un plug-in base l'origine dei plug-in dell'API di controllo (in precedenza detta anche l'API di MSSCCI), che fornisce la funzionalità di controllo di origine di base quando si usa Visual Studio origine controllo utente (interfaccia INTERFACCIA UTENTE). Un controllo del codice sorgente VSPackage, d'altra parte, offre una nuova, deep-integrazione [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] percorso adatto per l'integrazione del controllo codice sorgente che richiede un elevato livello di complessità e autonomia nel modello di controllo relativa origine.  
  
 ![Cenni preliminari sul controllo di origine](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente  
 Tutte le versioni di Visual Studio supportano l'API dei plug-in del controllo origine versione della specifica 1.2 come un percorso di integrazione. Un implementatore di plug-in del controllo origine scrive una DLL che implementa le funzioni API dei plug-in del controllo origine per l'integrazione del controllo codice sorgente e la registrazione come descritto in [creazione di un plug-in controllo sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md). Questo approccio, l'ambiente di sviluppo integrato (IDE) usa il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dell'interfaccia utente per le finestre di dialogo, ad esempio archiviazione, l'estrazione, pagine delle proprietà di strumenti/opzioni, le barre degli strumenti e i glifi di controllo di origine. Aderendo all'API dei plug-in del controllo origine assicura un'integrazione semplice in Visual Studio e un'esperienza senza problemi per l'utente. Ciò significa che il plug-in del controllo del codice sorgente deve implementare la maggior parte delle funzioni e i callback dettagliati nell'API.  
  
 Per implementare un controllo del codice sorgente del plug-in usando l'API dei plug-in del controllo origine, seguire questa procedura:  
  
1. Creare una DLL che implementa le funzioni specificate nei [Plug-in controllo del codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2. Registrare la DLL, rendendo le voci del Registro di sistema (descritto in [come: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Creare un file di supporto dell'interfaccia utente e la visualizzazione quando viene richiesto dal pacchetto di scheda di controllo di origine (il componente di Visual Studio che gestisce la funzionalità di controllo sorgente tramite plug-in controllo codice sorgente)  
  
   In risposta a un comando di controllo di origine, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni per il controllo del codice sorgente del plug-in tramite le funzioni definite nell'API dei plug-in controllo di origine. Per le opzioni avanzate, il plug-in del controllo del codice sorgente può essere chiamata su per presentare la propria interfaccia utente, ad esempio, di esplorazione per un progetto di controllo del codice sorgente. Ciò significa che l'utente possibile che venga visualizzata due potenzialmente diversi stili dell'interfaccia utente quando si lavora con controllo del codice sorgente: l'interfaccia utente che presenta Visual Studio e l'interfaccia utente che presenta il plug-in del controllo del codice sorgente. Ciò è più evidente con operazioni di controllo avanzate.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvenienti legati all'implementazione di un plug-in del controllo del codice sorgente  
  
- Per le funzionalità avanzate, l'utente può visualizzare due diversi stili di interfacce, causando possibili confusioni.  
  
- Il plug-in del controllo del codice sorgente è limitata al modello di controllo di origine in cui è inclusa l'API dei plug-in del controllo origine.  
  
- L'API dei plug-in del controllo origine potrebbero essere troppo restrittiva per alcuni scenari di controllo di origine.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in del controllo del codice sorgente  
  
- Visual Studio fornisce l'interfaccia utente per tutte le operazioni di controllo di origine di base in modo che il plug-in del controllo del codice sorgente non è necessario implementare interfacce utente potenzialmente complesse.  
  
- A causa dell'API strict, il plug-in del controllo del codice sorgente può interagire facilmente con i programmi di controllo di origine esterna per offrire funzionalità più estese; Visual Studio non è rilevante troppo molto come il controllo del codice sorgente viene eseguita, solo che viene eseguito in base all'API dei plug-in del controllo origine.  
  
- È più semplice implementare un controllo del codice sorgente del plug-in rispetto a un pacchetto VSPackage di controllo di origine.  
  
## <a name="source-control-vspackage"></a>VSPackage di controllo codice sorgente  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Consente di integrazione completa con Visual Studio con controllo completo del controllo del codice sorgente e la sostituzione completa dell'interfaccia utente controllo origine fornita da Visual Studio. Un controllo del codice sorgente VSPackage è stato registrato con Visual Studio e fornisce funzionalità di controllo di origine. Sebbene controllo del codice sorgente diversi pacchetti VSPackage può essere registrato con Visual Studio, solo uno di essi può essere attivo in qualsiasi momento. Un pacchetto VSPackage di controllo di origine dispone del controllo completo sul controllo del codice sorgente e l'aspetto in Visual Studio mentre è attiva. Tutti gli altri controllo del codice sorgente pacchetti VSPackage che possono essere registrati nel sistema sono inattivo e non verrà visualizzata alcuna interfaccia utente affatto.  
  
 Implementazione di un controllo del codice sorgente VSPackage richiede una strategia di "tutto o niente". Il creatore di un pacchetto VSPackage di controllo di origine deve investire una quantità significativa di lavoro richiesto nell'implementazione di un numero di interfacce di controllo di origine e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intero di controllo del codice sorgente. Visualizzare [creazione di un VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md) per altri dettagli.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvenienti legati all'implementazione di un VSPackage di controllo del codice sorgente  
  
- Il pacchetto VSPackage deve implementare un numero di interfacce complesse da integrare correttamente con Visual Studio.  
  
- Il pacchetto VSPackage deve fornire tutte l'interfaccia utente necessaria per controllo del codice sorgente; Visual Studio non offre alcuna assistenza in quest'area.  
  
- Un controllo del codice sorgente VSPackage è strettamente associato a Visual Studio e non può funzionare con i programmi autonomi, in modo che la funzionalità non può essere condivisi facilmente con una versione del programma di controllo di origine esterna.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un VSPackage di controllo del codice sorgente  
  
- Poiché il pacchetto VSPackage dispone di funzionalità e controllo completo sul controllo del codice sorgente dell'interfaccia utente, l'utente viene visualizzata un'interfaccia trasparente per controllo del codice sorgente.  
  
- Il pacchetto VSPackage non è limitato a un modello di controllo di origine specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)   
 [Creazione di un controllo del codice sorgente del plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novità del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)
