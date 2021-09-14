---
title: Registrazione e selezione (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni su come registrare un VSPackage del controllo del codice sorgente con Visual Studio e su come selezionare il pacchetto da caricare da più pacchetti di controllo del codice sorgente registrati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 23a64b0432c5a77f764ae7ef83e1c0ed9d604c2f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709505"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e selezione (VSPackage di controllo del codice sorgente)
Un VSPackage del controllo del codice sorgente deve essere registrato per esporlo a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Se è registrato più vspackage del controllo del codice sorgente, l'utente può selezionare il pacchetto VSPackage da caricare in momenti appropriati. Per altri dettagli sui pacchetti VSPackage e su come registrarli, vedere [VSPackage.](../../extensibility/internals/vspackages.md)

## <a name="registering-a-source-control-package"></a>Registrazione di un pacchetto di controllo del codice sorgente
 Il pacchetto di controllo del codice sorgente viene registrato in modo che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'ambiente possa trovarlo ed eseguire query per le funzionalità supportate. Questo è conforme a uno schema di caricamento ritardato in cui un'istanza di un pacchetto viene creata solo quando le funzionalità o i comandi sono necessari o richiesti in modo esplicito.

 I pacchetti VSPackage posizionano le informazioni in una chiave del Registro di sistema specifica della versione, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X.Y,* dove *X* è il numero di versione principale e *Y* è il numero di versione secondaria. Questa procedura consente di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 L'interfaccia utente supporta la selezione tra più plug-in di controllo del codice sorgente installati (tramite il pacchetto dell'adattatore di controllo del codice sorgente) e pacchetti VSPackage del controllo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del codice sorgente. Può essere presente un solo plug-in o VSPackage del controllo del codice sorgente attivo alla volta. Tuttavia, come descritto di seguito, l'IDE consente il passaggio tra i plug-in del controllo del codice sorgente e i pacchetti VSPackage tramite un meccanismo di scambio automatico dei pacchetti basato su soluzione. Per abilitare questo meccanismo di selezione, il pacchetto VSPackage del controllo del codice sorgente deve soddisfare alcuni requisiti.

### <a name="registry-entries"></a>Voci del Registro di sistema
 Un pacchetto di controllo del codice sorgente richiede tre GUID privati:

- GUID pacchetto: GUID principale per il pacchetto che contiene l'implementazione del controllo del codice sorgente (ID_Package in questa sezione).

- GUID del controllo del codice sorgente: SI tratta di un GUID per il pacchetto VSPackage del controllo del codice sorgente usato per la registrazione con lo stub del controllo del codice sorgente di Visual Studio e viene usato anche come GUID del contesto dell'interfaccia utente del comando. Il GUID del servizio di controllo del codice sorgente viene registrato nel GUID del controllo del codice sorgente. Nell'esempio il GUID del controllo del codice sorgente è denominato ID_SccProvider.

- GUID del servizio di controllo del codice sorgente: si tratta del GUID del servizio privato usato da Visual Studio (denominato SID_SccPkgService in questa sezione). Inoltre, il pacchetto di controllo del codice sorgente deve definire altri GUID per VSPackage, finestre degli strumenti e così via.

  Le voci del Registro di sistema seguenti devono essere effettuate da un VSPackage del controllo del codice sorgente:

| Nome della chiave | Voci |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (impostazione predefinita) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (impostazione predefinita) = rg_sz:\<Friendly name of Package><br /><br /> Service = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (impostazione predefinita) = rg_sz: #\<Resource ID for localized name><br /><br /> Package = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> Si noti che il nome della chiave, `SourceCodeControl` , è già usato da e non è disponibile come scelta per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<PackageName> . | (impostazione predefinita) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto di controllo del codice sorgente
 Diversi plug-in basati su API del controllo del codice sorgente e pacchetti VSPackage di controllo del codice sorgente possono essere registrati contemporaneamente. Il processo di selezione di un plug-in di controllo del codice sorgente o di UN VSPackage deve garantire che carichi il plug-in o il VSPackage nel momento appropriato e possa rinviare il caricamento dei componenti non necessari fino a quando non [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sono necessari. Inoltre, deve rimuovere tutta l'interfaccia utente da altri VSPackage inattivi, incluse le voci di menu, le finestre di dialogo e le barre degli strumenti, e visualizzare l'interfaccia utente per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage attivo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un VSPackage del controllo del codice sorgente quando viene eseguita una delle operazioni seguenti:

- La soluzione viene aperta (quando la soluzione è nel controllo del codice sorgente).

   Quando viene aperta una soluzione o un progetto nel controllo del codice sorgente, l'IDE causa il caricamento del pacchetto VSPackage del controllo del codice sorgente designato per la soluzione.

- Viene eseguito uno dei comandi di menu del pacchetto VSPackage del controllo del codice sorgente.

  Un pacchetto VSPackage del controllo del codice sorgente deve caricare tutti i componenti necessari solo quando verranno effettivamente usati (altrimenti noti come caricamento ritardato).

### <a name="automatic-solution-based-vspackage-swapping"></a>Scambio automatico di pacchetti VSPackage basati su soluzioni
 È possibile scambiare manualmente i pacchetti VSPackage del controllo del codice sorgente tramite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **finestra di** dialogo Opzioni nella **categoria Controllo del** codice sorgente. Lo scambio automatico dei pacchetti basati su soluzioni significa che un pacchetto di controllo del codice sorgente designato per una determinata soluzione viene impostato automaticamente come attivo all'apertura della soluzione. Ogni pacchetto di controllo del codice sorgente deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> implementare e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce il passaggio tra i plug-in del controllo del codice sorgente (implementazione dell'API plug-in del controllo del codice sorgente) e i pacchetti VSPackage del controllo del codice sorgente.

 Il pacchetto dell'adattatore di controllo del codice sorgente viene usato per passare a qualsiasi plug-in basato sull'API del plug-in del controllo del codice sorgente. Il processo di passaggio al pacchetto intermedio dell'adattatore di controllo del codice sorgente e di determinazione del plug-in del controllo del codice sorgente che deve essere impostato su attivo o inattivo è trasparente per l'utente. Il pacchetto dell'adapter è sempre attivo quando è attivo un plug-in del controllo del codice sorgente. Il passaggio tra due plug-in del controllo del codice sorgente consente di caricare e scaricare semplicemente la DLL del plug-in. Il passaggio a un vspackage del controllo del codice sorgente, tuttavia, comporta l'interazione con l'IDE per caricare il VSPackage appropriato.

 Un VSPackage del controllo del codice sorgente viene chiamato quando viene aperta una soluzione e la chiave del Registro di sistema per il pacchetto VSPackage si trova nel file della soluzione. Quando la soluzione viene aperta, trova [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il valore del Registro di sistema e carica il pacchetto VSPackage del controllo del codice sorgente appropriato. Tutti i pacchetti VSPackage del controllo del codice sorgente devono avere le voci del Registro di sistema descritte in precedenza. Una soluzione nel controllo del codice sorgente è contrassegnata come associata a un pacchetto VSPackage del controllo del codice sorgente specifico. I pacchetti VSPackage del controllo del codice sorgente devono <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> implementare per abilitare lo scambio automatico dei pacchetti VSPackage basati su soluzioni.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio Interfaccia utente per la selezione e il cambio di pacchetto
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un'interfaccia utente per il vspackage del controllo del codice sorgente e la selezione di plug-in nella **finestra di** dialogo Opzioni nella categoria Controllo del codice **sorgente.** Consente all'utente di selezionare il plug-in del controllo del codice sorgente attivo o il pacchetto VSPackage. Un elenco a discesa include:

- Tutti i pacchetti di controllo del codice sorgente installati

- Tutti i plug-in del controllo del codice sorgente installati

- Opzione "none", che disabilita il controllo del codice sorgente

  È visibile solo l'interfaccia utente per la scelta del controllo del codice sorgente attivo. La selezione di VSPackage nasconde l'interfaccia utente per il pacchetto VSPackage precedente e mostra l'interfaccia utente per il nuovo pacchetto. Il pacchetto VSPackage attivo viene selezionato per singolo utente. Se un utente ha più copie di aperte contemporaneamente, ognuna può [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potenzialmente usare un VSPackage attivo diverso. Se più utenti sono connessi allo stesso computer, ogni utente può avere istanze separate di aperte, ognuna con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un VSPackage attivo diverso. Quando più istanze di vengono chiuse da un utente, il pacchetto VSPackage del controllo del codice sorgente attivo per l'ultima soluzione aperta diventa il pacchetto VSPackage del controllo del codice sorgente predefinito, da impostare come attivo al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] riavvio.

  A differenza delle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , il riavvio dell'IDE non è più l'unico modo per cambiare i pacchetti VSPackage del controllo del codice sorgente. La selezione del pacchetto VSPackage è automatica. Il cambio di pacchetto richiede Windows privilegi utente (non amministratore o power user).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)
- [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
