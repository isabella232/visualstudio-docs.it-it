---
title: Finestra di progettazione dei comandi . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709651"
---
# <a name="command-design"></a>Progettazione dei comandi
Quando si aggiunge un comando a un VSPackage, è necessario specificare dove deve essere visualizzato, quando è disponibile e come deve essere gestito.

## <a name="define-commands"></a>Definire i comandi
 Per definire nuovi comandi, includere un file della tabella dei comandi di Visual Studio (*vsct*) nel progetto VSPackage. Se è stato creato un pacchetto VSPackage utilizzando il modello di pacchetto di Visual Studio, il progetto include uno di questi file. Per ulteriori informazioni, vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio unisce tutti i file *vsct trovati* in modo che possa visualizzare i comandi. Poiché questi file sono distinti dal file binario VSPackage, Visual Studio non è necessario caricare il pacchetto per trovare i comandi. Per ulteriori informazioni, vedere [Come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> usa l'attributo registration per definire le risorse di menu e i comandi. Per ulteriori informazioni, vedere [Implementazione dei](../../extensibility/internals/command-implementation.md)comandi .

 I comandi possono essere modificati in fase di esecuzione in diversi modi. Possono essere visualizzati o nascosti, abilitati o disabilitati. Possono visualizzare testo o icone diverse o contenere valori diversi. Una grande quantità di personalizzazione può essere eseguita prima di Visual Studio carica il pacchetto VSPackage.A great deal of customization may be performed before Visual Studio loads your VSPackage. Per ulteriori informazioni, vedere [Come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Gestori di comandi
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, è necessario instradarlo in modo appropriato. Instradamento di un comando significa inviarlo al pacchetto VSPackage corretto per abilitarlo o disabilitarlo, nasconderlo o visualizzarlo ed eseguirlo se l'utente sceglie di farlo. Per ulteriori informazioni, consultate [Algoritmo di routing dei](../../extensibility/internals/command-routing-algorithm.md)comandi.

## <a name="visual-studio-command-environment"></a>Ambiente dei comandi di Visual StudioVisual Studio command environment
 Visual Studio può ospitare un numero qualsiasi di VSPackage e ognuno può contribuire il proprio set di comandi. L'ambiente visualizza solo i comandi appropriati per l'attività corrente. Per ulteriori informazioni, consultate [Disponibilità dei comandi](../../extensibility/internals/command-availability.md) e Oggetti [contesto di selezione.](../../extensibility/internals/selection-context-objects.md)

 Un pacchetto VSPackage che definisce nuovi comandi, menu, barre degli strumenti o menu di scelta rapida fornisce le informazioni sui comandi per Visual Studio in fase di installazione tramite le voci del Registro di sistema che fanno riferimento alle risorse in assembly nativi o gestiti. Ogni risorsa fa quindi riferimento a un file di risorse di dati binari (*.cto*), che viene prodotto quando si compila un file di tabella dei comandi di Visual Studio (*.vsct*). In questo modo Visual Studio per fornire set di comandi uniti, menu e barre degli strumenti senza dover caricare ogni VSPackage installato.

### <a name="command-organization"></a>Organizzazione dei comandi
 L'ambiente posiziona i comandi per gruppo, priorità e menu.

- I gruppi sono raccolte logiche di comandi correlati, ad esempio il gruppo di comandi **Taglia**, **Copia**e **Incolla.** I gruppi sono i comandi visualizzati nei menu.

- La priorità determina l'ordine in cui i singoli comandi di un gruppo vengono visualizzati nel menu.

- I menu fungono da contenitori per i gruppi.

  L'ambiente predefinisce alcuni comandi, gruppi e menu. Per ulteriori informazioni, consultate [Comando predefinito, posizionamento](../../extensibility/internals/default-command-group-and-toolbar-placement.md)di gruppi e barre degli strumenti.

  Un comando può essere assegnato a un gruppo primario. Il gruppo primario controlla la posizione del comando nella struttura del menu principale e nella finestra di dialogo **Personalizza.** Un comando può essere visualizzato in più gruppi; ad esempio, un comando può trovarsi nel menu principale, in un menu di scelta rapida e in una barra degli strumenti. Per ulteriori informazioni, vedere [Come VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Routing dei comandi
 Il processo di richiamo e routing dei comandi per VSPackage differisce dal processo di chiamata di metodi su istanze di oggetti.

 L'ambiente indirizza i comandi in sequenza dal contesto di comando più interno (locale), basato sulla selezione corrente, al contesto più esterno (globale). Il primo contesto in grado di eseguire il comando è quello che lo gestisce. Per ulteriori informazioni, consultate [Algoritmo di routing dei](../../extensibility/internals/command-routing-algorithm.md)comandi.

 Nella maggior parte dei casi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'ambiente gestisce i comandi utilizzando l'interfaccia . Poiché lo schema di routing dei <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comandi consente a molti oggetti diversi di gestire i comandi, può essere implementato da un numero qualsiasi di oggetti. questi includono controlli Microsoft ActiveX, implementazioni di visualizzazione della finestra, oggetti documento, gerarchie di progetto e gli oggetti VSPackage stessi (per i comandi globali). In alcuni casi specializzati, ad esempio i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> comandi di routing in una gerarchia, l'interfaccia deve essere implementata.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Implementazione dei comandi](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un pacchetto VSPackage.Describes how to implement commands in a VSPackage.|
|[Disponibilità dei comandi](../../extensibility/internals/command-availability.md)|Viene descritto come il contesto di Visual Studio determina quali comandi sono disponibili.|
|[Algoritmo di routing dei comandi](../../extensibility/internals/command-routing-algorithm.md)|Viene descritto come l'architettura di routing dei comandi di Visual Studio consente ai comandi di essere gestiti da diversi vsPackage.Describes how Visual Studio command routing architecture enables commands to be handled by different VSPackages.|
|[Linee guida per il posizionamento dei comandi](../../extensibility/internals/command-placement-guidelines.md)|Viene illustrato come posizionare i comandi nell'ambiente di Visual Studio.|
|[Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Viene descritto come VSPackage possono utilizzare al meglio l'architettura dei comandi di Visual Studio.Describes how VSPackages can best utilize the Visual Studio command architecture.|
|[Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Viene descritto come VSPackage possono utilizzare al meglio i comandi inclusi in Visual Studio.|
|[Gestire VSPackage](../../extensibility/managing-vspackages.md)|Viene descritto come Visual Studio carica VSPackage.Describes how Visual Studio loads VSPackages.|
|[File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornisce informazioni sui file *vsct* basati su XML, utilizzati per descrivere il layout e l'aspetto dei comandi nei package VS.|
