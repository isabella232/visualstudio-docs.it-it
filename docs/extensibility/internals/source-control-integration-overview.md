---
title: Cenni preliminari sull'integrazione del controllo del codice sorgente - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705115"
---
# <a name="source-control-integration-overview"></a>Panoramica dell'integrazione del controllo del codice sorgente
In questa sezione vengono confrontati i due modi per integrare nel controllo del codice sorgente di Visual Studio; un controllo del codice sorgente Plug-in e un VSPackage che fornisce una soluzione di controllo del codice sorgente ed evidenzia le nuove funzionalità del controllo del codice sorgente. Visual Studio consente il passaggio manuale tra il controllo del codice sorgente VSPackage e plug-in controllo del codice sorgente, nonché la commutazione automatica basata su soluzione.

## <a name="source-control-integration"></a>Integrazione del controllo del codice sorgente
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta due tipi di opzioni di integrazione del controllo del codice sorgente. In tutte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le versioni di , è comunque possibile integrare un plug-in basato sull'API del plug-in del controllo del codice sorgente (precedentemente definita anche API MSSCCI), che fornisce funzionalità di controllo del codice sorgente di base durante l'utilizzo dell'interfaccia utente del controllo del codice sorgente di Visual Studio. Un controllo del codice sorgente VSPackage, d'altra [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] parte, fornisce un nuovo percorso di integrazione completa adatto per l'integrazione del controllo del codice sorgente che richiede un elevato livello di sofisticazione e autonomia nel modello di controllo del codice sorgente.

 ![Cenni preliminari sul controllo del codice sorgente](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Plug-in del controllo del codice sorgente
 Tutte le versioni di Visual Studio supportano la versione 1.2 della specifica dell'API del plug-in del controllo del codice sorgente come percorso di integrazione. Un implementatore del plug-in del controllo del codice sorgente scrive una DLL che implementa le funzioni API del plug-in del controllo del codice sorgente per l'integrazione e la registrazione del controllo del codice sorgente, come descritto in [Creazione di un plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)del controllo del codice sorgente . In questo approccio, l'ambiente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sviluppo integrato (IDE) utilizza l'interfaccia utente per le finestre di dialogo, ad esempio archiviazione, estrazione, pagine delle proprietà strumenti/opzioni, barre degli strumenti e glifi del controllo del codice sorgente. L'aderenza rigorosa all'API del plug-in del controllo del codice sorgente assicura una facile integrazione in Visual Studio e un'esperienza senza problemi per l'utente. Ciò significa che il plug-in del controllo del codice sorgente deve implementare la maggior parte delle funzioni e callback dettagliati nell'API.

 Per implementare un plug-in del controllo del codice sorgente utilizzando l'API plug-in controllo del codice sorgente, attenersi alla seguente procedura:

1. Creare una DLL che implementa le funzioni specificate nei [plug-in](../../extensibility/source-control-plug-ins.md)del controllo del codice sorgente .

2. Registrare la DLL creando le voci del Registro di sistema appropriate (descritte in [Procedura: installare un plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)del controllo del codice sorgente ).

3. Creare un'interfaccia utente helper e visualizzare quando richiesto dal pacchetto dell'adattatore del controllo del codice sorgente (il componente di Visual Studio che gestisce la funzionalità del controllo del codice sorgente tramite i plug-in del controllo del codice sorgente)Create a helper UI and display when prompted by the Source Control Adapter Package (the Visual Studio component that handles source control functionality via source control plug-in)

   In risposta a un comando del controllo del codice sorgente, l'IDE di Visual Studio presenta un'interfaccia utente standard per le operazioni di base e quindi passa le informazioni al plug-in del controllo del codice sorgente tramite le funzioni definite nell'API del plug-in del controllo del codice sorgente. Per le opzioni avanzate, il plug-in del controllo del codice sorgente può essere chiamato per presentare la propria interfaccia utente, ad esempio, la ricerca di un progetto di controllo del codice sorgente. Ciò significa che l'utente può essere presentato con due stili possibilmente diversi dell'interfaccia utente quando si tratta di controllo del codice sorgente: l'interfaccia utente che presenta Visual Studio e l'interfaccia utente che presenta il plug-in controllo del codice sorgente. Ciò è più evidente con le operazioni avanzate di controllo del codice sorgente.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Drawback per l'implementazione di un plug-in del controllo del codice sorgente

- Per le funzionalità avanzate, l'utente può vedere due diversi stili di interfacce, causando possibile confusione.

- Il plug-in del controllo del codice sorgente è limitato al modello di controllo del codice sorgente implicito dall'API del plug-in del controllo del codice sorgente.

- L'API del plug-in del controllo del codice sorgente potrebbe essere troppo restrittiva per alcuni scenari di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantaggi dell'implementazione di un plug-in per il controllo del codice sorgente

- Visual Studio fornisce tutta l'interfaccia utente per tutte le operazioni di controllo del codice sorgente di base in modo che il plug-in del controllo del codice sorgente non è necessario implementare l'interfaccia utente potenzialmente complessa.

- A causa dell'API rigorosa, il plug-in del controllo del codice sorgente può interagire facilmente con programmi di controllo del codice sorgente esterni per fornire funzionalità più estese; Visual Studio non si preoccupa troppo come viene eseguita la funzionalità di controllo del codice sorgente, solo che viene eseguita in base all'API plug-in controllo del codice sorgente.

- È più semplice implementare un plug-in del controllo del codice sorgente rispetto a un controllo del codice sorgente VSPackage.It is easier to implement a source control plug-in than a source control VSPackage.

## <a name="source-control-vspackage"></a>Controllo del codice sorgente VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]consente un'integrazione completa in Visual Studio con il controllo completo delle funzionalità del controllo del codice sorgente e la sostituzione completa dell'interfaccia utente del controllo del codice sorgente fornita da Visual Studio. Un controllo del codice sorgente VSPackage viene registrato con Visual Studio e fornisce funzionalità di controllo del codice sorgente. Anche se più controllo del codice sorgente VSPackage possono essere registrati con Visual Studio, solo uno di essi può essere attivo in qualsiasi momento. Un controllo del codice sorgente VSPackage ha il controllo completo sulla funzionalità del controllo del codice sorgente e l'aspetto in Visual Studio mentre è attivo. Tutti gli altri VSPackage di controllo del codice sorgente che possono essere registrati nel sistema sono inattivi e non verrà visualizzata alcuna interfaccia utente a tutti.

 Implementazione di un controllo del codice sorgente VSPackage richiede una strategia "tutto o niente". Il creatore di un controllo del codice sorgente VSPackage deve investire una quantità significativa di sforzo nell'implementazione di una serie di interfacce di controllo del codice sorgente e nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente. Vedere [creazione di un controllo del codice sorgente VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) per ulteriori dettagli.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Drawback per implementare un controllo del codice sorgente VSPackage

- Il pacchetto VSPackage deve implementare una serie di interfacce complesse per integrarsi correttamente con Visual Studio.The VSPackage must implement a number of complex interfaces to integrate successfully with Visual Studio.

- Il pacchetto VSPackage deve fornire tutta l'interfaccia utente necessaria per il controllo del codice sorgente; Visual Studio non fornirà assistenza in quest'area.

- Un controllo del codice sorgente VSPackage è intimamente legato a Visual Studio e non può funzionare con programmi autonomi, pertanto la funzionalità non può essere facilmente condivisa con una versione esterna del programma di controllo del codice sorgente.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantaggi dell'implementazione di un controllo del codice sorgente VSPackage

- Poiché il pacchetto VSPackage ha il controllo completo sull'interfaccia utente del controllo del codice sorgente e la funzionalità, l'utente viene presentato con un'interfaccia senza problemi per il controllo del codice sorgente.

- Il pacchetto VSPackage non è limitato a un particolare modello di controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Controllo del codice sorgente](../../extensibility/internals/source-control.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novità del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-source-control.md)
