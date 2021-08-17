---
title: Progettazione dei comandi | Microsoft Docs
description: Informazioni su come progettare un comando per un VSPackage in Visual Studio. Incluso, come specificare dove viene visualizzato, quando è disponibile e come deve essere gestito.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c02049819487df474898c2c40319ed4a6d13db294ed5d34da84743c0eb4b50a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376261"
---
# <a name="command-design"></a>Progettazione dei comandi
Quando si aggiunge un comando a un VSPackage, è necessario specificare dove deve essere visualizzato, quando è disponibile e come deve essere gestito.

## <a name="define-commands"></a>Definire i comandi
 Per definire nuovi comandi, includere un file Visual Studio tabella comandi (*vsct*) nel progetto VSPackage. Se è stato creato un VSPackage usando il modello Visual Studio pacchetto, il progetto include uno di questi file. Per altre informazioni, vedere Visual Studio file di tabella dei comandi [(con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio unisce tutti i file *vsct* trovati in modo che possa visualizzare i comandi. Poiché questi file sono distinti dal file binario VSPackage, Visual Studio non è necessario caricare il pacchetto per trovare i comandi. Per altre informazioni, vedere [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente.](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Visual Studio l'attributo <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> di registrazione per definire le risorse di menu e i comandi. Per altre informazioni, vedere [Implementazione dei comandi](../../extensibility/internals/command-implementation.md).

 I comandi possono essere modificati in fase di esecuzione in diversi modi. Possono essere visualizzati o nascosti, abilitati o disabilitati. Possono visualizzare testo o icone diversi o contenere valori diversi. È possibile eseguire una grande quantità di personalizzazione prima Visual Studio caricare il pacchetto VSPackage. Per altre informazioni, vedere [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente.](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

## <a name="command-handlers"></a>Gestori di comandi
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, deve essere indirizzato in modo appropriato. Instradare un comando significa inviarlo al pacchetto VSPackage corretto per abilitarlo o disabilitarlo, nasconderlo o visualizzarlo ed eseguirlo se l'utente sceglie di farlo. Per altre informazioni, vedere [Algoritmo di routing dei comandi](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Visual Studio comando
 Visual Studio possibile ospitare un numero qualsiasi di VSPackage e ognuno può contribuire al proprio set di comandi. L'ambiente visualizza solo i comandi appropriati per l'attività corrente. Per altre informazioni, vedere [Disponibilità dei comandi e](../../extensibility/internals/command-availability.md) Oggetti di contesto di [selezione](../../extensibility/internals/selection-context-objects.md).

 Un VSPackage che definisce nuovi comandi, menu, barre degli strumenti o menu di scelta rapida fornisce le informazioni di comando al Visual Studio in fase di installazione tramite voci del Registro di sistema che fanno riferimento alle risorse in assembly nativi o gestiti. Ogni risorsa fa quindi riferimento a un file di risorse dati binari (con estensione *cto),* che viene generato quando si compila un file Visual Studio tabella dei comandi *(vsct).* Ciò consente Visual Studio di fornire set di comandi, menu e barre degli strumenti uniti senza dover caricare ogni VSPackage installato.

### <a name="command-organization"></a>Organizzazione dei comandi
 L'ambiente posiziona i comandi per gruppo, priorità e menu.

- I gruppi sono raccolte logiche di comandi correlati, ad esempio il gruppo di comandi **Taglia,** **Copia** **e** Incolla. I gruppi sono i comandi visualizzati nei menu.

- La priorità determina l'ordine in cui i singoli comandi di un gruppo vengono visualizzati nel menu.

- I menu fungono da contenitori per i gruppi.

  L'ambiente predefinisce alcuni comandi, gruppi e menu. Per altre informazioni, vedere [Posizionamento predefinito di comandi, gruppi e barre degli strumenti.](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

  Un comando può essere assegnato a un gruppo primario. Il gruppo primario controlla la posizione del comando nella struttura del menu principale e nella **finestra di dialogo** Personalizza. Un comando può essere visualizzato in più gruppi. Ad esempio, un comando può essere nel menu principale, in un menu di scelta rapida e in una barra degli strumenti. Per altre informazioni, vedere [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente.](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

### <a name="command-routing"></a>Routing dei comandi
 Il processo di chiamata e routing dei comandi per i pacchetti VSPackage è diverso dal processo di chiamata dei metodi nelle istanze dell'oggetto.

 L'ambiente indirizza i comandi in sequenza dal contesto di comando più interno (locale), basato sulla selezione corrente, al contesto più esterno (globale). Il primo contesto in grado di eseguire il comando è quello che lo gestisce. Per altre informazioni, vedere [Algoritmo di routing dei comandi](../../extensibility/internals/command-routing-algorithm.md).

 Nella maggior parte dei casi, l'ambiente gestisce i comandi usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia . Poiché lo schema di routing dei comandi consente a molti oggetti diversi di gestire i comandi, può essere implementato da un numero qualsiasi di oggetti, tra cui i controlli di Microsoft ActiveX, le implementazioni della visualizzazione finestra, gli oggetti documento, le gerarchie di progetto e gli oggetti VSPackage stessi (per i comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> globali). In alcuni casi specifici, ad esempio i comandi di routing in una gerarchia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> l'interfaccia deve essere implementata.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Implementazione del comando](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un vspackage.|
|[Disponibilità dei comandi](../../extensibility/internals/command-availability.md)|Descrive in che modo Visual Studio contesto determina quali comandi sono disponibili.|
|[Algoritmo di routing dei comandi](../../extensibility/internals/command-routing-algorithm.md)|Descrive come Visual Studio di routing dei comandi consente di gestire i comandi da vspackage diversi.|
|[Linee guida per il posizionamento dei comandi](../../extensibility/internals/command-placement-guidelines.md)|Suggerisce come posizionare i comandi nell'Visual Studio locale.|
|[Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descrive come i pacchetti VSPackage possono usare al meglio l'architettura Visual Studio comando.|
|[Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descrive come i pacchetti VSPackage possono usare al meglio i comandi inclusi in Visual Studio.|
|[Gestire VSPackage](../../extensibility/managing-vspackages.md)|Viene descritto come Visual Studio vspackage.|
|[Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornisce informazioni sui file con estensione *vsct* basati su XML, usati per descrivere il layout e l'aspetto dei comandi nei pacchetti VSPackage.|
