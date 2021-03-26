---
title: Configurazione del progetto per l'output | Microsoft Docs
description: Informazioni sui processi di compilazione supportati da ogni configurazione e sulle interfacce e sui metodi in base ai quali è possibile rendere disponibili gli elementi di output.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13e37999ad9f3bada375c1897207e1e4c15546e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082010"
---
# <a name="project-configuration-for-output"></a>Configurazione del progetto per l'output
Ogni configurazione può supportare un set di processi di compilazione che generano elementi di output, ad esempio file eseguibili o file di risorse. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che collegano i tipi di output correlati, ad esempio i file eseguibili (con estensione exe, dll, lib) e i file di origine (file con estensione IDL, h).

 Gli elementi di output possono essere resi disponibili tramite i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metodi ed enumerati con i <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodi. Quando si desidera raggruppare gli elementi di output, il progetto deve implementare anche l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaccia.

 Il costrutto sviluppato implementando `IVsOutputGroup` consente ai progetti di raggruppare gli output in base all'utilizzo. Ad esempio, una DLL può essere raggruppata con il relativo database di programma (PDB).

> [!NOTE]
> Un file PDB contiene informazioni di debug e viene creato quando si specifica l'opzione ' genera informazioni di debug ' durante la compilazione del file con estensione dll o exe. Il file con estensione PDB viene in genere generato solo per la configurazione del progetto di debug.

 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supportata, anche se il numero di output contenuti in un gruppo può variare dalla configurazione alla configurazione. Ad esempio, la DLL del progetto di Matt potrebbe includere mattd.dll e opaco. pdb nella configurazione di debug, ma includere solo matt.dll nella configurazione della versione finale.

 I gruppi hanno anche le stesse informazioni sull'identificatore, ad esempio il nome canonico, il nome visualizzato e le informazioni sul gruppo, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente la distribuzione e la creazione di pacchetti per continuare a funzionare anche se le configurazioni cambiano.

 I gruppi possono anche avere un output della chiave che consente ai collegamenti per la creazione di pacchetti di puntare a elementi significativi. Tutti i gruppi potrebbero essere vuoti in una determinata configurazione, pertanto non è necessario fare supposizioni sulle dimensioni di un gruppo. Le dimensioni (numero di output) di ogni gruppo in qualsiasi configurazione possono essere diverse da quelle di un altro gruppo nella stessa configurazione. Può anche essere diversa dalle dimensioni dello stesso gruppo in un'altra configurazione.

 ![Rappresentazione grafica di gruppi di output](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Gruppi di output

 L'uso principale dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaccia consiste nel fornire l'accesso per compilare, distribuire ed eseguire il debug di oggetti di gestione e consentire ai progetti la libertà di raggruppare gli output. Per ulteriori informazioni sull'utilizzo di questa interfaccia, vedere [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Nel diagramma precedente, il gruppo compilato ha un output chiave tra le configurazioni (bD.exe o b.exe), in modo che l'utente possa creare un collegamento a compilato e sappia che il collegamento funzionerà indipendentemente dalla configurazione distribuita. L'origine del gruppo non dispone di un output della chiave, pertanto l'utente non può creare un collegamento. Se il gruppo di debug compilato dispone di un output della chiave, ma il gruppo di distribuzione non è stato compilato, l'implementazione potrebbe non essere corretta. Segue, quindi, che se una configurazione include un gruppo che non contiene output e, di conseguenza, nessun file di chiave, le altre configurazioni con quel gruppo che contengono output non possono avere file di chiave. Gli editor del programma di installazione presuppongono che i nomi canonici e i nomi visualizzati dei gruppi, oltre all'esistenza di un file di chiave, non cambiano in base alle configurazioni.

 Si noti che se un progetto ha un `IVsOutputGroup` che non vuole creare un pacchetto o distribuirlo, è sufficiente non inserire l'output in un gruppo. L'output può comunque essere enumerato normalmente implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodo che restituisce tutti gli output di una configurazione indipendentemente dal raggruppamento.

 Per ulteriori informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di progetto personalizzato in [MPF per i progetti](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
