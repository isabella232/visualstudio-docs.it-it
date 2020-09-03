---
title: Progettazione comandi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195069"
---
# <a name="command-design"></a>Progettazione dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si aggiunge un comando a un VSPackage, è necessario specificare dove deve essere visualizzato, quando è disponibile e come gestirlo.  
  
## <a name="defining-commands"></a>Definizione di comandi  
 Per definire nuovi comandi, includere un file della tabella dei comandi di Visual Studio (con estensione vsct) nel progetto VSPackage. Se è stato creato un pacchetto VSPackage usando il modello di pacchetto di Visual Studio, il progetto include uno di questi file. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio unisce tutti i file con estensione vsct individuati in modo che possano visualizzare i comandi. Poiché questi file sono distinti dal binario VSPackage, Visual Studio non deve caricare il pacchetto per trovare i comandi. Per ulteriori informazioni, vedere [come i VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio usa l' <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attributo di registrazione per definire le risorse di menu e i comandi. Per ulteriori informazioni, vedere [implementazione](../../extensibility/internals/command-implementation.md)di.  
  
 I comandi possono essere modificati in fase di esecuzione in diversi modi. Possono essere visualizzati o nascosti, abilitati o disabilitati. Possono visualizzare testo o icone diverse o contenere valori diversi. È possibile che venga eseguita una grande personalizzazione prima che Visual Studio carichi il pacchetto VSPackage. Per ulteriori informazioni, vedere [come i VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestori di comandi  
 Quando si crea un comando, è necessario specificare un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, deve essere indirizzato in modo appropriato. Il routing di un comando significa inviarlo al pacchetto VSPackage corretto per abilitarlo o disabilitarlo, nasconderlo o visualizzarlo ed eseguirlo se l'utente sceglie di eseguire questa operazione. Per ulteriori informazioni, vedere [algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Ambiente dei comandi di Visual Studio  
 Visual Studio può ospitare un numero qualsiasi di pacchetti VSPackage e ognuno può contribuire al proprio set di comandi. Nell'ambiente vengono visualizzati solo i comandi appropriati per l'attività corrente. Per altre informazioni, vedere [oggetti Context di selezione](../../extensibility/internals/selection-context-objects.md)e [disponibilità](../../extensibility/internals/command-availability.md) .  
  
 Un pacchetto VSPackage che definisce i nuovi comandi, i menu, le barre degli strumenti o i menu di scelta rapida fornisce le informazioni sul comando a Visual Studio al momento dell'installazione tramite le voci del registro di sistema che fanno riferimento a risorse in assembly nativi o gestiti. Ogni risorsa fa quindi riferimento a un file di risorse binarie (con estensione CTO), che viene generato quando si compila un file della tabella dei comandi di Visual Studio (con estensione vsct). Questo consente a Visual Studio di fornire set di comandi, menu e barre degli strumenti Uniti senza dover caricare tutti i pacchetti VSPackage installati.  
  
### <a name="command-organization"></a>Organizzazione comandi  
 L'ambiente posiziona i comandi per gruppo, priorità e menu.  
  
- I gruppi sono raccolte logiche di comandi correlati, ad esempio il gruppo di comandi **taglia**, **copia**e **Incolla** . I gruppi sono i comandi visualizzati nei menu.  
  
- La priorità determina l'ordine in cui vengono visualizzati i singoli comandi di un gruppo nel menu.  
  
- I menu fungono da contenitori per i gruppi.  
  
  L'ambiente predefinisce alcuni comandi, gruppi e menu. Per ulteriori informazioni, vedere [comando predefinito, gruppo e posizionamento della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Un comando può essere assegnato a un gruppo primario. Il gruppo primario controlla la posizione del comando nella struttura del menu principale e nella finestra di dialogo **Personalizza** . Un comando può essere visualizzato in più gruppi; ad esempio, un comando può essere nel menu principale, in un menu di scelta rapida e su una barra degli strumenti. Per ulteriori informazioni, vedere [come i VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>comandi (routing)  
 Il processo di richiamo e routing dei comandi per i pacchetti VSPackage differisce dal processo di chiamata dei metodi nelle istanze degli oggetti.  
  
 L'ambiente instrada i comandi in sequenza dal contesto del comando più interno (locale), che è basato sulla selezione corrente, al contesto più esterno (globale). Il primo contesto che è in grado di eseguire il comando è quello che lo gestisce. Per ulteriori informazioni, vedere [algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).  
  
 Nella maggior parte dei casi, l'ambiente gestisce i comandi tramite l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Poiché lo schema di routing dei comandi consente a molti oggetti diversi di gestire i comandi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> può essere implementato da un numero qualsiasi di oggetti, tra cui i controlli ActiveX Microsoft, le implementazioni di visualizzazione finestre, gli oggetti documento, le gerarchie di progetto e gli oggetti VSPackage (per i comandi globali). In alcuni casi specializzati, ad esempio, i comandi di routing in una gerarchia, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia deve essere implementata.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Implementazione](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un VSPackage.|  
|[Disponibilità](../../extensibility/internals/command-availability.md)|Viene descritto il modo in cui il contesto di Visual Studio determina quali comandi sono disponibili.|  
|[Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md)|Descrive il modo in cui l'architettura di routing dei comandi di Visual Studio consente di gestire i comandi da VSPackage diversi.|  
|[Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)|Suggerisce come posizionare i comandi nell'ambiente Visual Studio.|  
|[Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descrive in che modo i pacchetti VSPackage possono usare al meglio l'architettura dei comandi di Visual Studio.|  
|[Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descrive in che modo i pacchetti VSPackage possono usare al meglio i comandi inclusi in Visual Studio.|  
|[Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)|Descrive il modo in cui Visual Studio carica i pacchetti VSPackage.|  
|[File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornisce informazioni sui file con estensione vsct basati su XML, usati per descrivere il layout e l'aspetto dei comandi nei pacchetti VSPackage.|
