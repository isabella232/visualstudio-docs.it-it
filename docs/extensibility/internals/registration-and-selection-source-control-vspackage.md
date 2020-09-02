---
title: Registrazione e selezione (VSPackage del controllo del codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705713"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e selezione (VSPackage di controllo del codice sorgente)
Un VSPackage del controllo del codice sorgente deve essere registrato per esporlo a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Se è registrato più di un VSPackage del controllo del codice sorgente, l'utente può selezionare il VSPackage da caricare in momenti appropriati. Vedere [VSPackage](../../extensibility/internals/vspackages.md) per altre informazioni sui pacchetti VSPackage e su come registrarli.

## <a name="registering-a-source-control-package"></a>Registrazione di un pacchetto di controllo del codice sorgente
 Il pacchetto del controllo del codice sorgente viene registrato in modo che l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente possa trovarlo ed eseguire una query per le funzionalità supportate. Questo è conforme allo schema di caricamento ritardato in cui viene creata un'istanza di un pacchetto solo quando le funzionalità o i comandi sono necessari o sono richiesti in modo esplicito.

 I pacchetti VSPackage inseriscono informazioni in una chiave del registro di sistema specifica della versione, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. Y*, dove *x* è il numero di versione principale e *Y* è il numero di versione secondario. Questa procedura consente di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente supporta la selezione tra più plug-in del controllo del codice sorgente installati (tramite il pacchetto di adattatore del controllo del codice sorgente) e i pacchetti VSPackage del controllo del codice sorgente. Può essere presente un solo plug-in del controllo del codice sorgente attivo o VSPackage alla volta. Tuttavia, come descritto di seguito, l'IDE consente il passaggio tra i plug-in del controllo del codice sorgente e i pacchetti VSPackage tramite un meccanismo automatico di scambio di pacchetti basato su soluzioni. Per abilitare questo meccanismo di selezione sono necessari alcuni requisiti per il pacchetto VSPackage del controllo del codice sorgente.

### <a name="registry-entries"></a>Voci del Registro di sistema
 Un pacchetto di controllo del codice sorgente necessita di tre GUID privati:

- GUID del pacchetto: si tratta del GUID principale del pacchetto che contiene l'implementazione del controllo del codice sorgente (denominata ID_Package in questa sezione).

- GUID del controllo del codice sorgente: si tratta di un GUID per il VSPackage del controllo del codice sorgente usato per la registrazione allo stub del controllo del codice sorgente di Visual Studio e viene usato anche come GUID del contesto dell'interfaccia utente del comando. Il GUID del servizio del controllo del codice sorgente è registrato nel GUID del controllo del codice sorgente. Nell'esempio, il GUID del controllo del codice sorgente viene chiamato ID_SccProvider.

- GUID del servizio di controllo del codice sorgente: è il GUID del servizio privato usato da Visual Studio, denominato SID_SccPkgService in questa sezione. Inoltre, il pacchetto del controllo del codice sorgente deve definire altri GUID per i pacchetti VSPackage, le finestre degli strumenti e così via.

  Le seguenti voci del registro di sistema devono essere effettuate da un pacchetto VSPackage del controllo del codice sorgente:

| Nome chiave | Voci |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (impostazione predefinita) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (impostazione predefinita) = rg_sz:\<Friendly name of Package><br /><br /> Service = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (impostazione predefinita) = rg_sz: #\<Resource ID for localized name><br /><br /> Pacchetto = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> Si noti che il nome della chiave, `SourceCodeControl` , è già utilizzato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e non è disponibile come scelta per \<PackageName> . | (impostazione predefinita) = rg_sz: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto di controllo del codice sorgente
 Diversi plug-in del controllo del codice sorgente e i pacchetti VSPackage basati sull'API possono essere registrati simultaneamente. Il processo di selezione di un plug-in del controllo del codice sorgente o di un pacchetto VSPackage deve garantire che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carichi il plug-in o il pacchetto VSPackage al momento appropriato e può rinviare il caricamento dei componenti superflui fino a quando non sono necessari. Inoltre, è [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] necessario rimuovere tutte le interfacce utente da altri pacchetti VSPackage inattivi, incluse le voci di menu, le finestre di dialogo e le barre degli strumenti e visualizzare l'interfaccia utente per il pacchetto VSPackage attivo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un VSPackage del controllo del codice sorgente quando viene eseguita una delle operazioni seguenti:

- La soluzione viene aperta (quando la soluzione è sotto il controllo del codice sorgente).

   Quando si apre una soluzione o un progetto nel controllo del codice sorgente, l'IDE causa il caricamento del pacchetto VSPackage del controllo del codice sorgente designato per la soluzione.

- Viene eseguito uno dei comandi di menu del pacchetto VSPackage del controllo del codice sorgente.

  Un pacchetto VSPackage del controllo del codice sorgente deve caricare tutti i componenti necessari solo quando vengono effettivamente usati (altrimenti noto come caricamento ritardato).

### <a name="automatic-solution-based-vspackage-swapping"></a>Scambio automatico di pacchetti VSPackage basati su soluzioni
 È possibile scambiare manualmente i pacchetti VSPackage del controllo del codice sorgente tramite la finestra di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dialogo **Opzioni** sotto la categoria **controllo del codice sorgente** . Lo scambio automatico di pacchetti basato su soluzione significa che un pacchetto di controllo del codice sorgente designato per una particolare soluzione viene impostato automaticamente su attivo al momento dell'apertura della soluzione. Ogni pacchetto del controllo del codice sorgente deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce l'opzione tra i plug-in del controllo del codice sorgente (implementazione dell'API del plug-in del controllo del codice sorgente) e i pacchetti VSPackage del controllo del codice sorgente

 Il pacchetto dell'adattatore del controllo del codice sorgente viene utilizzato per passare a qualsiasi plug-in del controllo del codice sorgente basato sull'API. Il processo di passaggio al pacchetto di adattatori del controllo del codice sorgente intermedio e determinare quale plug-in del controllo del codice sorgente deve essere impostato su attivo o inattivo è trasparente per l'utente. Il pacchetto dell'adapter è sempre attivo quando è attivo un plug-in del controllo del codice sorgente. Il cambio tra due plug-in del controllo del codice sorgente equivale a caricare e scaricare semplicemente la DLL del plug-in. Il trasferimento a un VSPackage del controllo del codice sorgente comporta tuttavia l'interazione con l'IDE per caricare il pacchetto VSPackage appropriato.

 Un pacchetto VSPackage del controllo del codice sorgente viene chiamato quando viene aperta una soluzione e la chiave del registro di sistema per il pacchetto VSPackage si trova nel file di soluzione. Quando la soluzione viene aperta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individua il valore del registro di sistema e carica il pacchetto VSPackage del controllo del codice sorgente appropriato. Tutti i VSPackage del controllo del codice sorgente devono avere le voci del registro di sistema descritte sopra. Una soluzione nel controllo del codice sorgente è contrassegnata come associata a un particolare VSPackage del controllo del codice sorgente. I pacchetti VSPackage del controllo del codice sorgente devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> per abilitare lo swapping automatico del pacchetto VSPackage basato su soluzione.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaccia utente di Visual Studio per la selezione e il cambio di pacchetti
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un'interfaccia utente per la selezione del pacchetto di controllo del codice sorgente e del plug-in nella finestra di dialogo **Opzioni** sotto la categoria **controllo del codice sorgente** . Consente all'utente di selezionare il plug-in o il pacchetto VSPackage attivo del controllo del codice sorgente. Un elenco a discesa include:

- Tutti i pacchetti del controllo del codice sorgente installati

- Tutti i plug-in del controllo del codice sorgente installati

- Opzione "None", che disabilita il controllo del codice sorgente

  È visibile solo l'interfaccia utente per la scelta del controllo del codice sorgente attivo. La selezione del pacchetto VSPackage nasconde l'interfaccia utente per il pacchetto VSPackage precedente e Mostra l'interfaccia utente per quella nuova. Il pacchetto VSPackage attivo è selezionato per ogni singolo utente. Se un utente dispone di più copie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aperte simultaneamente, ciascuna di esse può usare potenzialmente un VSPackage attivo diverso. Se più utenti sono connessi allo stesso computer, ogni utente può disporre di istanze separate di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Open, ognuna con un VSPackage attivo diverso. Quando più istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono chiuse da un utente, il pacchetto VSPackage del controllo del codice sorgente che era attivo per l'ultima soluzione aperta diventa il VSPackage predefinito del controllo del codice sorgente, da impostare come attivo al riavvio.

  Diversamente dalle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , un riavvio dell'IDE non è più l'unico modo per cambiare i pacchetti VSPackage del controllo del codice sorgente. La selezione del pacchetto VSPackage è automatica. Il cambio di pacchetti richiede privilegi utente di Windows (non amministratore o utente Power).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
