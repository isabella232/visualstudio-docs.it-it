---
title: Configurazione del progetto per output | Microsoft Docs
description: Informazioni sui processi di compilazione che ogni configurazione può supportare e sulle interfacce e i metodi con cui gli elementi di output possono essere resi disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899875"
---
# <a name="project-configuration-for-output"></a>Configurazione del progetto per l'output
Ogni configurazione può supportare un set di processi di compilazione che producono elementi di output, ad esempio file eseguibili o di risorse. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che collegano tipi correlati di output, ad esempio file eseguibili (.exe, .dll, lib) e file di origine (file con estensione idl, h).

 Gli elementi di output possono essere resi disponibili <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> tramite i metodi ed enumerati con i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> . Quando si desidera raggruppare gli elementi di output, il progetto deve implementare anche <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> l'interfaccia .

 Il costrutto sviluppato implementando consente `IVsOutputGroup` ai progetti di raggruppare gli output in base all'utilizzo. Ad esempio, una DLL potrebbe essere raggruppata con il relativo database di programma (PDB).

> [!NOTE]
> Un file PDB contiene informazioni di debug e viene creato quando si specifica l'opzione "Genera informazioni di debug" durante la compilazione del .dll o .exe. Il file con estensione pdb viene in genere generato solo per la configurazione del progetto di debug.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta, anche se il numero di output contenuti in un gruppo può variare da una configurazione all'altro. Ad esempio, la DLL del progetto Matt potrebbe includere mattd.dll e mattd.pdb nella configurazione di debug, ma includere solo matt.dll nella configurazione Retail.

 I gruppi hanno anche le stesse informazioni sull'identificatore, ad esempio nome canonico, nome visualizzato e informazioni sui gruppi, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente alla distribuzione e alla creazione di pacchetti di continuare a funzionare anche se le configurazioni cambiano.

 I gruppi possono anche avere un output chiave che consente ai collegamenti di creazione pacchetti di puntare a un elemento significativo. Qualsiasi gruppo potrebbe essere vuoto in una determinata configurazione, quindi non è consigliabile fare ipotesi sulle dimensioni di un gruppo. Le dimensioni (numero di output) di ogni gruppo in qualsiasi configurazione possono essere diverse dalle dimensioni di un altro gruppo nella stessa configurazione. Può anche essere diverso dalle dimensioni dello stesso gruppo in un'altra configurazione.

 ![Grafico Gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Gruppi di output

 L'uso principale dell'interfaccia è fornire l'accesso per compilare, distribuire ed eseguire il debug di oggetti di gestione e consentire ai progetti la libertà <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> di raggruppare gli output. Per altre informazioni sull'uso di questa interfaccia, vedere [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Nel diagramma precedente, Group Built ha un output chiave tra le configurazioni (bD.exe o b.exe) in modo che l'utente possa creare un collegamento a Compilato e sapere che il collegamento funzionerà indipendentemente dalla configurazione distribuita. L'origine gruppo non ha un output chiave, quindi l'utente non può creare un collegamento. Se debug Group Built ha un output chiave, ma retail Group Built no, si tratta di un'implementazione non corretta. Ne consegue quindi che se una configurazione ha un gruppo che non contiene output e, di conseguenza, nessun file di chiave, le altre configurazioni con tale gruppo che contengono output non possono avere file di chiave. Gli editor del programma di installazione presuppongono che i nomi canonici e i nomi visualizzati dei gruppi, oltre all'esistenza di un file di chiave, non cambino in base alle configurazioni.

 Si noti che se un progetto dispone di un che non vuole creare un pacchetto o distribuire, è sufficiente non inserire `IVsOutputGroup` l'output in un gruppo. L'output può comunque essere enumerato normalmente implementando il metodo che restituisce tutti gli output di una configurazione indipendentemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> dal raggruppamento.

 Per altre informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di progetto personalizzato in [MPF for Projects.](https://github.com/tunnelvisionlabs/MPFProj10)

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
