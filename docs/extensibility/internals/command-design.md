---
title: Comando Design | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42b41ee59f842c277400ba03ff682a757d5343e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009830"
---
# <a name="command-design"></a>Progettazione dei comandi
Quando si aggiunge un comando a un pacchetto VSPackage, è necessario specificare dove verrà visualizzato quando è disponibile e come deve essere gestito.  
  
## <a name="define-commands"></a>Definire i comandi  
 Per definire nuovi comandi, includere una tabella di comandi di Visual Studio (*vsct*) file nel progetto di VSPackage. Se è stato creato un pacchetto VSPackage usando il modello di pacchetto di Visual Studio, il progetto include uno di questi file. Per altre informazioni, vedere [file table (vsct) di Visual Studio comando](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio unisce tutti i *vsct* file si trova in modo che sia possibile visualizzare i comandi. Poiché questi file sono diversi dal VSPackage binario, Visual Studio è necessario caricare il pacchetto per trovare i comandi. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio Usa il <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attributo di registrazione per definire le risorse del menu e comandi. Per altre informazioni, vedere [implementazione di comandi](../../extensibility/internals/command-implementation.md).  
  
 I comandi possono essere modificati in fase di esecuzione in diversi modi diversi. Possano essere visualizzate o nascoste, abilitati o disabilitati. È possibile visualizzare un testo diverso o icone o contengono valori diversi. È possibile eseguire una grande quantità di personalizzazione prima di Visual Studio carica il pacchetto VSPackage. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestori di comandi  
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, devono essere indirizzata in modo appropriato. Routing di un comando significa inviarlo al pacchetto VSPackage corretto per abilitare o disabilitare questa, nascondere o visualizzarlo ed eseguirlo se l'utente sceglie di eseguire questa operazione. Per altre informazioni, vedere [algoritmo di routing di comandi](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="visual-studio-command-environment"></a>Ambiente di comando di Visual Studio  
 Visual Studio può ospitare qualsiasi numero di pacchetti VSPackage e ognuno può fornire un proprio set di comandi. L'ambiente consente di visualizzare solo i comandi appropriati per l'attività corrente. Per altre informazioni, vedere [comando disponibilità](../../extensibility/internals/command-availability.md) e [gli oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md).  
  
 Un pacchetto VSPackage che definisce nuovi comandi, menu, barre degli strumenti o menu di scelta rapida fornisce le informazioni sui comandi di Visual Studio al momento dell'installazione tramite le voci del Registro di sistema che fanno riferimento a risorse negli assembly nativo o gestito. Ogni risorsa fa quindi riferimento a una risorsa di dati binari (*CTO*) file, che viene generato quando si compila una tabella di comandi di Visual Studio (*con estensione vsct*) file. In questo modo Visual Studio per fornire il set di comandi unite, menu e barre degli strumenti senza dover caricare ogni VSPackage installati.  
  
### <a name="command-organization"></a>Comando dell'organizzazione  
 L'ambiente posiziona i comandi dal gruppo, alla priorità e menu.  
  
- I gruppi sono raccolte logiche di comandi correlati, ad esempio, il **tagliare**, **copia**, e **Incolla** del gruppo di comandi. I gruppi sono i comandi che vengono visualizzati nei menu.  
  
- La priorità determina l'ordine in cui singoli comandi in un gruppo visualizzato nel menu.  
  
- Menu fungono da contenitori per i gruppi.  
  
  L'ambiente sono disponibili alcuni comandi, gruppi e i menu. Per altre informazioni, vedere [posizionamento di comando, il gruppo e sulla barra degli strumenti predefinita](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Un comando può essere assegnato a un gruppo primario. Il gruppo primario consente di controllare la posizione del comando nella struttura di menu principale e nel **Personalizza** nella finestra di dialogo. Un comando può essere visualizzati in più gruppi. ad esempio, può essere un comando nel menu principale, in un menu di scelta rapida e una barra degli strumenti. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Routing dei comandi  
 Il processo di chiamata e routing dei comandi per pacchetti VSPackage è diverso dal processo di chiamata di metodi su istanze di oggetti.  
  
 L'ambiente consente di indirizzare i comandi in sequenza dal contesto del comando più interno (locale), che è basato sulla selezione corrente, per il contesto più esterno (globale). Il primo contesto che è in grado di eseguire il comando è quello che la gestisce. Per altre informazioni, vedere [algoritmo di routing di comandi](../../extensibility/internals/command-routing-algorithm.md).  
  
 Nella maggior parte dei casi, l'ambiente gestisce i comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Poiché lo schema di routing di comandi Abilita molti oggetti diversi gestire i comandi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> può essere implementata da un numero qualsiasi di oggetti; questi comprendono controlli Microsoft ActiveX, le implementazioni di visualizzazione finestra, gli oggetti di documenti, le gerarchie di progetto, e agli oggetti VSPackage se stessi (per i comandi globali). In alcuni casi speciali, ad esempio, routing dei comandi in una gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia deve essere implementata.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Implementazione del comando](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un pacchetto VSPackage.|  
|[Disponibilità dei comandi](../../extensibility/internals/command-availability.md)|Descrive come contesto di Visual Studio determina quali comandi sono disponibili.|  
|[Algoritmo di routing di comandi](../../extensibility/internals/command-routing-algorithm.md)|Descrive come architettura di routing di comandi di Visual Studio consente i comandi gestire i pacchetti VSPackage diversi.|  
|[Linee guida per il posizionamento di comando](../../extensibility/internals/command-placement-guidelines.md)|Suggerisce come posizionare i comandi nell'ambiente di Visual Studio.|  
|[Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Viene descritto come i VSPackage possono utilizzare al meglio l'architettura di comandi di Visual Studio.|  
|[Posizione di comando, il gruppo e sulla barra degli strumenti predefinita](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Viene descritto come i VSPackage possono meglio usare i comandi inclusi in Visual Studio.|  
|[Gestire i pacchetti VSPackage](../../extensibility/managing-vspackages.md)|Descrive la modalità di caricamento pacchetti VSPackage in Visual Studio.|  
|[File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornisce informazioni su basato su XML *vsct* file, che vengono usati per descrivere il layout e l'aspetto dei comandi nei pacchetti VSPackage.|