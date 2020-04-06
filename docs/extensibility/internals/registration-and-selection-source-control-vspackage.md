---
title: Registrazione e selezione (controllo del codice sorgente VSPackage) . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705713"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e selezione (VSPackage di controllo del codice sorgente)
Un controllo del codice sorgente VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve essere registrato per esporlo al . Se è registrato più di un controllo del codice sorgente VSPackage, l'utente può selezionare il pacchetto VSPackage da caricare nei momenti appropriati. Vedere [VSPackage](../../extensibility/internals/vspackages.md) per ulteriori dettagli sui pacchetti VSPackage e su come registrarli.

## <a name="registering-a-source-control-package"></a>Registrazione di un pacchetto del controllo del codice sorgenteRegistering a Source Control Package
 Il pacchetto del controllo del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] codice sorgente viene registrato in modo che l'ambiente possa trovarlo ed eseguire una query per le funzionalità supportate. Ciò è conforme a uno schema di caricamento ritardato in cui un'istanza di un pacchetto viene creata solo quando le relative funzionalità o comandi sono necessari o sono richiesti in modo esplicito.

 I package VS inserisce le informazioni in una chiave del\\Registro di sistema specifica della versione, HKEY_LOCAL_MACHINE*SOFTWARE,* dove *X* è il numero di versione principale e *Y* è il numero di versione secondario. Questa procedura consente di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 L'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente (UI) supporta la selezione tra più plug-in del controllo del codice sorgente installati (tramite il pacchetto dell'adattatore del controllo del codice sorgente) nonché il controllo del codice sorgente VSPackage. Può essere presente un solo plug-in del controllo del codice sorgente attivo o VSPackage alla volta. Tuttavia, come descritto di seguito, l'IDE consente il passaggio tra i plug-in del controllo del codice sorgente e VSPackage tramite un meccanismo automatico di scambio di pacchetti basato su soluzione. Esistono alcuni requisiti da parte del controllo del codice sorgente VSPackage per abilitare questo meccanismo di selezione.

### <a name="registry-entries"></a>Voci del Registro di sistema
 Un pacchetto di controllo del codice sorgente richiede tre GUID privati:A source control package needs three private GUIDs:

- GUID pacchetto: questo è il GUID principale per il pacchetto che contiene l'implementazione del controllo del codice sorgente (denominato ID_Package in questa sezione).

- GUID controllo del codice sorgente: si tratta di un GUID per il controllo del codice sorgente VSPackage utilizzato per la registrazione con il Visual Studio Source Control Stub e viene utilizzato anche come un comando GUID di contesto dell'interfaccia utente. Il GUID del servizio controllo del codice sorgente è registrato sotto il GUID del controllo del codice sorgente. Nell'esempio, il GUID del controllo del codice sorgente viene chiamato ID_SccProvider.

- GUID del servizio di controllo del codice sorgente: GUID servizio privato utilizzato da Visual Studio (denominato SID_SccPkgService in questa sezione). Inoltre, il pacchetto di controllo del codice sorgente deve definire altri GUID per VSPackage, finestre degli strumenti e così via.

  Le seguenti voci del Registro di sistema devono essere effettuate da un controllo del codice sorgente VSPackage:The following registry entries must be made by a source control VSPackage:

| Nome della chiave | Voci |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (impostazione predefinita) : rg_sz ID_SccProvider: |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (impostazione predefinita)\<- rg_sz: nome descrittivo del pacchetto><br /><br /> Servizio rg_sz: SID_SccPkgService |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (impostazione predefinita)\<: rg_sz: ID risorsa per il nome localizzato><br /><br /> Pacchetto rg_sz ID_Package: |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> Si noti che `SourceCodeControl`il nome della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiave, , è \<già utilizzato da e non è disponibile come scelta per PackageName>. | (impostazione predefinita) : rg_sz ID_Package: |

## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto di controllo del codice sorgenteSelecting a Source Control Package
 Diversi plug-in basati sull'API del controllo del codice sorgente e i pacchetti VS del controllo del codice sorgente possono essere registrati contemporaneamente. Il processo di selezione di un plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del controllo del codice sorgente o VSPackage deve garantire che carica il plug-in o VSPackage al momento appropriato e può rinviare il caricamento di componenti non necessari fino a quando non sono necessari. Inoltre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è necessario rimuovere tutta l'interfaccia utente da altri PACKAGE VS inattivi, incluse le voci di menu, finestre di dialogo e barre degli strumenti e visualizzare l'interfaccia utente per il pacchetto VSPackage attivo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carica un controllo del codice sorgente VSPackage quando viene eseguita una delle seguenti operazioni:

- La soluzione viene aperta (quando la soluzione è inclusi nel controllo del codice sorgente).

   Quando viene aperta una soluzione o un progetto incluso nel controllo del codice sorgente, l'IDE causa il controllo del codice sorgente VSPackage che è stato designato per tale soluzione da caricare.

- Vengono eseguiti tutti i comandi di menu del controllo del codice sorgente VSPackage.

  Un controllo del codice sorgente VSPackage deve caricare tutti i componenti necessari solo quando sono effettivamente intenzionati a essere utilizzato (altrimenti noto come caricamento ritardato).

### <a name="automatic-solution-based-vspackage-swapping"></a>Scambio automatico di VSPackage basato su soluzione
 È possibile scambiare manualmente il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controllo del codice sorgente VSPackage tramite il **Opzioni** finestra di dialogo sotto il **controllo del codice sorgente** categoria. Lo scambio automatico di pacchetti basato su soluzione significa che un pacchetto del controllo del codice sorgente designato per una determinata soluzione viene impostato automaticamente su attivo all'apertura di tale soluzione. Ogni pacchetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> controllo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>del codice sorgente deve implementare e . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gestisce lo switch tra entrambi i plug-in del controllo del codice sorgente (implementazione dell'API plug-in controllo del codice sorgente) e il controllo del codice sorgente VSPackage.

 Il pacchetto dell'adattatore del controllo del codice sorgente viene utilizzato per passare a qualsiasi plug-in basato sull'API del plug-in del controllo del codice sorgente. Il processo di passaggio al pacchetto intermedio dell'adattatore del controllo del codice sorgente e per determinare quale plug-in del controllo del codice sorgente deve essere impostato su attivo o inattivo è trasparente per l'utente. Il pacchetto dell'adapter è sempre attivo quando è attivo qualsiasi plug-in del controllo del codice sorgente. Il passaggio tra due plug-in del controllo del codice sorgente equivale semplicemente a caricare e scaricare la DLL del plug-in. Passaggio a un controllo del codice sorgente VSPackage, tuttavia, comporta l'interazione con l'IDE per caricare il pacchetto VSPackage appropriato.

 Un controllo del codice sorgente VSPackage viene chiamato quando viene aperta una soluzione e la chiave del Registro di sistema per il pacchetto VSPackage è nel file di soluzione. Quando la soluzione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene aperta, trova il valore del Registro di sistema e carica il controllo del codice sorgente appropriato VSPackage. Tutti i pacchetti VSPackage del controllo del codice sorgente devono avere le voci del Registro di sistema descritte in precedenza. A solution that is under source control is marked as being associated with a particular source control VSPackage. Controllo del codice sorgente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> VSPackage devono implementare il per abilitare lo scambio automatico di VSPackage basato su soluzione.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio UI for Package Selection and Switching
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un'interfaccia utente per il controllo del codice sorgente VSPackage e la selezione del plug-in nel **opzioni** finestra di dialogo sotto il **controllo del codice sorgente** categoria. Consente all'utente di selezionare il plug-in del controllo del codice sorgente attivo o VSPackage.It allows the user to select the active source control plug-in or VSPackage. Un elenco a discesa include:

- Tutti i pacchetti di controllo del codice sorgente installati

- Tutti i plug-in del controllo del codice sorgente installati

- Un'opzione "none", che disabilita il controllo del codice sorgente

  È visibile solo l'interfaccia utente per la scelta del controllo del codice sorgente attivo. La selezione VSPackage nasconde l'interfaccia utente per il pacchetto VSPackage precedente e mostra l'interfaccia utente per quello nuovo. Il pacchetto VSPackage attivo viene selezionato in base all'utente. Se un utente dispone [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di più copie di open contemporaneamente, ognuno può potenzialmente utilizzare un VSPackage attivo diverso. Se più utenti sono connessi allo stesso computer, ogni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente può avere istanze separate di aperto, ognuno con un VSPackage attivo diverso. Quando più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istanze di vengono chiuse da un utente, il controllo del codice sorgente VSPackage che era attivo per l'ultima soluzione aperta diventa il controllo del codice sorgente predefinito VSPackage, da impostare attivo al riavvio.

  A differenza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]delle versioni precedenti di , un riavvio dell'IDE non è più l'unico modo per passare il controllo del codice sorgente VSPackage. La selezione VSPackage è automatica. Il passaggio da un pacchetto all'altro richiede privilegi utente Windows (non amministratore o Power User).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)
