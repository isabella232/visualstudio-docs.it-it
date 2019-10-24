---
title: Configurazione del progetto per l'output | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b6337d82e51cf728d69f7aabb46e9d4444ec564
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725889"
---
# <a name="project-configuration-for-output"></a>Configurazione del progetto per l'output
Ogni configurazione può supportare un set di processi di compilazione che generano elementi di output, ad esempio file eseguibili o file di risorse. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che collegano i tipi di output correlati, ad esempio i file eseguibili (con estensione exe, dll, lib) e i file di origine (file con estensione IDL, h).

 Gli elementi di output possono essere resi disponibili tramite i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> ed enumerati con i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>. Quando si desidera raggruppare gli elementi di output, il progetto deve implementare anche l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>.

 Il costrutto sviluppato implementando `IVsOutputGroup` consente ai progetti di raggruppare gli output in base all'utilizzo. Ad esempio, una DLL può essere raggruppata con il relativo database di programma (PDB).

> [!NOTE]
> Un file PDB contiene informazioni di debug e viene creato quando si specifica l'opzione ' genera informazioni di debug ' durante la compilazione del file con estensione dll o exe. Il file con estensione PDB viene in genere generato solo per la configurazione del progetto di debug.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata, anche se il numero di output contenuti in un gruppo può variare dalla configurazione alla configurazione. Ad esempio, la DLL del progetto di Matt potrebbe includere mattd. dll e mattd. pdb nella configurazione di debug, ma includere solo Matt. dll nella configurazione per la vendita al dettaglio.

 I gruppi hanno anche le stesse informazioni sull'identificatore, ad esempio il nome canonico, il nome visualizzato e le informazioni sul gruppo, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente la distribuzione e la creazione di pacchetti per continuare a funzionare anche se le configurazioni cambiano.

 I gruppi possono anche avere un output della chiave che consente ai collegamenti per la creazione di pacchetti di puntare a elementi significativi. Tutti i gruppi potrebbero essere vuoti in una determinata configurazione, pertanto non è necessario fare supposizioni sulle dimensioni di un gruppo. Le dimensioni (numero di output) di ogni gruppo in qualsiasi configurazione possono essere diverse da quelle di un altro gruppo nella stessa configurazione. Può anche essere diversa dalle dimensioni dello stesso gruppo in un'altra configurazione.

 ![Rappresentazione grafica di gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Gruppi di output

 L'uso principale dell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> consiste nel fornire l'accesso per compilare, distribuire ed eseguire il debug di oggetti di gestione e consentire ai progetti la libertà di raggruppare gli output. Per ulteriori informazioni sull'utilizzo di questa interfaccia, vedere [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Nel diagramma precedente, il gruppo compilato dispone di un output chiave tra le configurazioni, ovvero bD. exe o b. exe, in modo che l'utente possa creare un collegamento a compilato e sappia che il collegamento funzionerà indipendentemente dalla configurazione distribuita. L'origine del gruppo non dispone di un output della chiave, pertanto l'utente non può creare un collegamento. Se il gruppo di debug compilato dispone di un output della chiave, ma il gruppo di distribuzione non è stato compilato, l'implementazione potrebbe non essere corretta. Segue, quindi, che se una configurazione include un gruppo che non contiene output e, di conseguenza, nessun file di chiave, le altre configurazioni con quel gruppo che contengono output non possono avere file di chiave. Gli editor del programma di installazione presuppongono che i nomi canonici e i nomi visualizzati dei gruppi, oltre all'esistenza di un file di chiave, non cambiano in base alle configurazioni.

 Si noti che se un progetto ha un `IVsOutputGroup` che non vuole creare un pacchetto o una distribuzione, è sufficiente non inserire l'output in un gruppo. È comunque possibile enumerare l'output in modo normale implementando il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> che restituisce tutti gli output di una configurazione indipendentemente dal raggruppamento.

 Per ulteriori informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di progetto personalizzato in [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)