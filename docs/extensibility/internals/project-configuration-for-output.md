---
title: Configurazione del progetto per l'output Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706661"
---
# <a name="project-configuration-for-output"></a>Configurazione del progetto per l'output
Ogni configurazione può supportare un set di processi di compilazione che producono elementi di output, ad esempio file eseguibili o di risorse. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che collegano tipi correlati di output, ad esempio file eseguibili (con estensione exe, dll, lib) e file di origine (file con estensione idl, h).

 Gli elementi di output <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> possono essere resi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> disponibili tramite i metodi ed enumerati con i metodi. Quando si desidera raggruppare gli elementi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> output, il progetto deve implementare anche l'interfaccia.

 Il costrutto `IVsOutputGroup` sviluppato mediante l'implementazione consente ai progetti di raggruppare gli output in base all'utilizzo. Ad esempio, una DLL potrebbe essere raggruppata con il relativo database di programma (PDB).

> [!NOTE]
> Un file PDB contiene informazioni di debug e viene creato quando viene specificata l'opzione 'Genera informazioni di debug' durante la compilazione del file DLL o EXE. Il file con estensione pdb viene in genere generato solo per la configurazione del progetto Debug.The .pdb file is usually generated for Debug project configuration only.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata, anche se il numero di output contenuti in un gruppo può variare da configurazione a configurazione. Ad esempio, la DLL del progetto Matt potrebbe includere mattd.dll e mattd.pdb nella configurazione Debug, ma includere solo matt.dll nella configurazione Retail.

 I gruppi hanno anche le stesse informazioni sull'identificatore, ad esempio il nome canonico, il nome visualizzato e le informazioni sul gruppo, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente alla distribuzione e alla creazione di pacchetti di continuare a funzionare anche se le configurazioni cambiano.

 I gruppi possono anche avere un output chiave che consente ai collegamenti di creazione di pacchetti di puntare a qualcosa di significativo. Qualsiasi gruppo potrebbe essere vuoto in una determinata configurazione, pertanto non è necessario fare supposizioni sulle dimensioni di un gruppo. La dimensione (numero di output) di ogni gruppo in qualsiasi configurazione può essere diversa da quella di un altro gruppo nella stessa configurazione. Può anche essere diverso dalle dimensioni dello stesso gruppo in un'altra configurazione.

 ![Grafico Gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups (gruppi di prodotti vsOutputGroups)") Gruppi di output

 L'utilizzo principale <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> dell'interfaccia consiste nel fornire l'accesso agli oggetti di gestione di compilazione, distribuzione ed debug e consentire ai progetti la libertà di raggruppare gli output. Per ulteriori informazioni sull'utilizzo di questa interfaccia, vedere [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md).

 Nel diagramma precedente, Group Built dispone di un output di tasti tra le configurazioni (bD.exe o b.exe) in modo che l'utente possa creare un collegamento a Built e sapere che il collegamento funzionerà indipendentemente dalla configurazione distribuita. Origine gruppo non dispone di un output di chiave, pertanto l'utente non può creare un collegamento ad esso. Se il gruppo di debug compilato dispone di un output di chiave, ma il gruppo di vendita al dettaglio compilato non, che sarebbe un'implementazione non corretta. Ne consegue che se una configurazione dispone di un gruppo che non contiene output e, di conseguenza, nessun file di chiave, le altre configurazioni con tale gruppo che contengono output non possono avere file di chiave. Gli editor del programma di installazione presuppongono che i nomi canonici e i nomi visualizzati dei gruppi, oltre all'esistenza di un file di chiave, non cambino in base alle configurazioni.

 Si noti che `IVsOutputGroup` se un progetto ha un che non vuole creare un pacchetto o distribuire, è sufficiente non inserire tale output in un gruppo. L'output può comunque essere <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> enumerato normalmente implementando il metodo che restituisce tutti gli output di una configurazione indipendentemente dal raggruppamento.

 Per ulteriori informazioni, vedere `IVsOutputGroup` l'implementazione di nell'esempio di progetto personalizzato in [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione soluzione](../../extensibility/internals/solution-configuration.md)
