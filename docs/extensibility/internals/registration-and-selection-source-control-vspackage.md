---
title: Registrazione e selezione (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98f246f68b4f22dfeb4ba1899edd79495aff37fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908899"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e selezione (VSPackage di controllo del codice sorgente)
Un pacchetto VSPackage deve essere registrata per esporla a controllo del codice sorgente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se più di un controllo del codice sorgente VSPackage è registrato, l'utente può selezionare quale VSPackage da caricare in momenti appropriati. Visualizzare [VSPackage](../../extensibility/internals/vspackages.md) per altre informazioni sui pacchetti VSPackage e come registrarle.

## <a name="registering-a-source-control-package"></a>La registrazione di un pacchetto controllo del codice sorgente
 Il pacchetto del controllo codice sorgente è registrato in modo che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente possa trovare e query per le funzionalità supportate. Si tratta in conformità con uno schema di caricamento ritardato in cui viene creata un'istanza di un pacchetto solo quando la funzionalità o i comandi sono obbligatori o vengono richiesti in modo esplicito.

 I pacchetti VSPackage di inserire informazioni in una chiave del Registro di sistema specifici della versione, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *X* è il numero di versione principale e una *Y* è il numero di versione secondario. Questa esercitazione offre la possibilità di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI) supporta la selezione tra più codice sorgente installato plug-in del controllo (tramite il pacchetto della scheda di controllo codice sorgente), nonché di controllo del codice sorgente pacchetti VSPackage. Può esistere un solo plug-in del controllo del codice sorgente attivo o VSPackage alla volta. Tuttavia, come descritto di seguito, l'IDE consente di alternare fra plug-in controllo codice sorgente e i pacchetti VSPackage tramite un automatico lo scambio pacchetto meccanismo basati su una soluzione. Esistono alcuni requisiti da parte di VSPackage di controllo del codice sorgente per abilitare questo meccanismo di selezione.

### <a name="registry-entries"></a>Voci del Registro di sistema
 Un pacchetto controllo del codice sorgente richiede tre GUID privato:

- GUID del pacchetto: Si tratta del GUID principale per il pacchetto che contiene l'implementazione del controllo (denominato ID_Package in questa sezione).

- Controllo del codice sorgente GUID: Questo è un GUID per il controllo del codice sorgente consente di registrare con lo Stub di controllo di Visual Studio origine pacchetto VSPackage e viene usato anche come un GUID di contesto dell'interfaccia utente comandi. Il GUID del servizio di controllo sorgente è registrato sotto il controllo del codice sorgente GUID. Nell'esempio, il controllo del codice sorgente GUID viene chiamato ID_SccProvider.

- GUID del servizio di controllo di origine: Si tratta del servizio privato GUID utilizzato da Visual Studio (detti SID_SccPkgService in questa sezione). Inoltre, il pacchetto del controllo codice sorgente deve definire altri GUID per i pacchetti VSPackage, finestre degli strumenti e così via.

  Da un pacchetto VSPackage di controllo di origine, è necessario effettuare le seguenti voci del Registro di sistema:

| Nome della chiave | Voci |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (default) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (impostazione predefinita) = rg_sz:\<nome descrittivo del pacchetto ><br /><br /> Service = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (impostazione predefinita) = rg_sz: &\<ID risorsa per nome localizzato ><br /><br /> Package = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Si noti che il nome della chiave `SourceCodeControl`, è già usato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e non è disponibile come scelta per \<PackageName >.) | (default) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto controllo del codice sorgente
 Diversi basato su API dei plug-in del controllo origine plug-in e i pacchetti VSPackage possono essere registrati contemporaneamente di controllo del codice sorgente. È necessario assicurarsi che il processo di selezione di un plug-in del controllo del codice sorgente o un pacchetto VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica il plug-in o VSPackage al momento opportuno, può rinviare il caricamento dei componenti non necessari fino a quando sono necessari. Inoltre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve rimuovere l'interfaccia utente da altri VSPackage inattivi, incluse le voci di menu, finestre di dialogo e le barre degli strumenti e visualizzare l'interfaccia utente per il pacchetto VSPackage attivo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Carica un pacchetto VSPackage di controllo di origine quando viene eseguita una delle operazioni seguenti:

- Soluzione è aperta (quando la soluzione nel controllo del codice sorgente).

   Quando si apre una soluzione o progetto incluso nel controllo del codice sorgente, l'IDE fa sì che il controllo del codice sorgente VSPackage che è stato designato per la soluzione da caricare.

- Vengono eseguiti i comandi di menu del pacchetto VSPackage di controllo del codice sorgente.

  Un controllo del codice sorgente che VSPackage verrà caricato tutti i componenti che saranno necessari solo quando effettivamente che stanno per essere usata (nota anche come il caricamento ritardato).

### <a name="automatic-solution-based-vspackage-swapping"></a>Lo scambio automatico VSPackage basati su soluzioni
 È possibile scambiare manualmente il codice sorgente pacchetti VSPackage mediante il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opzioni** nella finestra di dialogo il **controllo del codice sorgente** categoria. Lo scambio automatico dei pacchetti basati su soluzioni significa che un pacchetto del controllo codice sorgente che è stato progettato per una particolare soluzione viene automaticamente impostato su attivo quando tale soluzione è aperta. Ogni pacchetto controllo del codice sorgente deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce il passaggio tra entrambi plug-in del controllo (che implementa l'API dei plug-in del controllo origine) di origine e i pacchetti VSPackage di controllo del codice sorgente.

 Il pacchetto di scheda di controllo di origine viene usato per passare a qualsiasi basato su API dei plug-in del controllo origine plug-in. Il processo di passaggio per il pacchetto di scheda di controllo codice sorgente intermedia e determinare quale plug-in del controllo del codice sorgente deve essere impostato su Attiva o inattiva è trasparente all'utente. Il pacchetto dell'adattatore è sempre attivo quando è attiva qualsiasi plug-in del controllo del codice sorgente. Il passaggio tra due quantità di plug-in di controllo di origine semplicemente il caricamento e scaricamento di DLL del plug-in. Passa a un pacchetto VSPackage di controllo di origine, tuttavia, prevede l'interazione con l'IDE a caricare il pacchetto VSPackage appropriato.

 Un controllo del codice sorgente VSPackage viene chiamato quando viene aperta una soluzione e la chiave del Registro di sistema per il pacchetto VSPackage è nel file di soluzione. Quando la soluzione è aperta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva che il valore del Registro di sistema e carica il controllo del codice sorgente appropriato package VS. Controllo del codice sorgente tutti i pacchetti VSPackage debba avere le voci del Registro di sistema descritte in precedenza. Una soluzione che si trova sotto controllo del codice sorgente viene contrassegnata come da associare a un controllo del codice sorgente particolare pacchetto VSPackage. I pacchetti VSPackage devono implementare controllo del codice sorgente di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> per abilitare automatico basati su una soluzione VSPackage la sostituzione.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaccia utente per la selezione del pacchetto e il cambio di Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'interfaccia utente per controllo del codice sorgente VSPackage e selezione plug-nel **le opzioni** nella finestra di dialogo il **controllo del codice sorgente** categoria. Consente all'utente di selezionare il plug-in del controllo del codice sorgente attivo o di un VSPackage. Un elenco di riepilogo a discesa include:

- Tutti i pacchetti del controllo del codice sorgente installato

- Tutti i plug-in controllo codice sorgente installato

- "none" opzione, che disabilita il controllo del codice sorgente

  È visibile solo l'interfaccia utente per la scelta di controllo di origine attiva. La selezione di VSPackage nasconde l'interfaccia utente per il pacchetto VSPackage precedente e viene illustrata l'interfaccia utente per quella nuova. Il pacchetto VSPackage attivo è selezionato per ogni utente. Se un utente dispone di più copie di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aperte contemporaneamente, ognuno di essi può comportare l'utilizzo un pacchetto VSPackage attivo diversi. Se più utenti sono connessi allo stesso computer, ogni utente può avere istanze separate di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aprire, ognuno con un pacchetto VSPackage attivo diversi. Quando più istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siano chiusi da un utente, il controllo del codice sorgente VSPackage che era attivo per la soluzione open ultima diventa il controllo del codice sorgente predefinito VSPackage, da impostare active al riavvio.

  Diversamente dalle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], riavviare l'IDE non è più l'unico modo per passare i pacchetti VSPackage controllo del codice sorgente. Selezione pacchetto VSPackage è automatica. Commutazione di pacchetti richiede privilegi di utente di Windows (non amministratore o utente esperto).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)