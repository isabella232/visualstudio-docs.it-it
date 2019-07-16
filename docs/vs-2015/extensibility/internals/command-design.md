---
title: Comando Design | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195069"
---
# <a name="command-design"></a>Progettazione dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando si aggiunge un comando a un pacchetto VSPackage, è necessario specificare dove verrà visualizzato quando è disponibile e come deve essere gestito.  
  
## <a name="defining-commands"></a>Definizione di comandi  
 Per definire nuovi comandi, includere un file di Visual Studio Command Table (vsct) nel progetto VSPackage. Se è stato creato un pacchetto VSPackage usando il modello di pacchetto di Visual Studio, il progetto include uno di questi file. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio unisce tutti i file con estensione vsct che rileva in modo che sia possibile visualizzare i comandi. Poiché questi file sono diversi dal VSPackage binario, Visual Studio è necessario caricare il pacchetto per trovare i comandi. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio Usa il <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> attributo di registrazione per definire le risorse del menu e comandi. Per altre informazioni, vedere [implementazione](../../extensibility/internals/command-implementation.md).  
  
 I comandi possono essere modificati in fase di esecuzione in diversi modi diversi. Possano essere visualizzate o nascoste, abilitati o disabilitati. È possibile visualizzare un testo diverso o icone o contengono valori diversi. È possibile eseguire una grande quantità di personalizzazione prima di Visual Studio carica il pacchetto VSPackage. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Gestori di comandi  
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando. Se l'utente seleziona il comando, devono essere indirizzata in modo appropriato. Routing di un comando significa inviarlo al pacchetto VSPackage corretto per abilitare o disabilitare questa, nascondere o visualizzarlo ed eseguirlo se l'utente sceglie di eseguire questa operazione. Per altre informazioni, vedere [algoritmo di Routing](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Ambiente di comando di Visual Studio  
 Visual Studio può ospitare qualsiasi numero di pacchetti VSPackage e ognuno può fornire un proprio set di comandi. L'ambiente consente di visualizzare solo i comandi appropriati per l'attività corrente. Per altre informazioni, vedere [disponibilità](../../extensibility/internals/command-availability.md) e [selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md).  
  
 Un pacchetto VSPackage che definisce nuovi comandi, menu, barre degli strumenti o menu di scelta rapida fornisce le informazioni sui comandi di Visual Studio al momento dell'installazione tramite le voci del Registro di sistema che fanno riferimento a risorse negli assembly nativo o gestito. Ogni risorsa fa quindi riferimento a un file di risorse (CTO) i dati binari, che viene generato quando si compila un file di Visual Studio Command Table (vsct). In questo modo Visual Studio per fornire il set di comandi unite, menu e barre degli strumenti senza dover caricare ogni VSPackage installati.  
  
### <a name="command-organization"></a>Comando dell'organizzazione  
 L'ambiente posiziona i comandi dal gruppo, alla priorità e menu.  
  
- I gruppi sono raccolte logiche di comandi correlati, ad esempio, il **tagliare**, **copia**, e **Incolla** del gruppo di comandi. I gruppi sono i comandi che vengono visualizzati nei menu.  
  
- La priorità determina l'ordine in cui singoli comandi in un gruppo visualizzato nel menu.  
  
- Menu fungono da contenitori per i gruppi.  
  
  L'ambiente sono disponibili alcuni comandi, gruppi e i menu. Per altre informazioni, vedere [comandi predefiniti, gruppo e posizione della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Un comando può essere assegnato a un gruppo primario. Il gruppo primario consente di controllare la posizione del comando nella struttura di menu principale e nel **Personalizza** nella finestra di dialogo. Un comando può essere visualizzati in più gruppi. ad esempio, può essere un comando nel menu principale, in un menu di scelta rapida e una barra degli strumenti. Per altre informazioni, vedere [modo in cui i pacchetti VSPackage aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>comandi (routing)  
 Il processo di chiamata e routing dei comandi per pacchetti VSPackage è diverso dal processo di chiamata di metodi su istanze di oggetti.  
  
 L'ambiente consente di indirizzare i comandi in sequenza dal contesto del comando più interno (locale), che è basato sulla selezione corrente, per il contesto più esterno (globale). Il primo contesto che è in grado di eseguire il comando è quello che la gestisce. Per altre informazioni, vedere [algoritmo di Routing](../../extensibility/internals/command-routing-algorithm.md).  
  
 Nella maggior parte dei casi, l'ambiente gestisce i comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Poiché lo schema di routing di comandi Abilita molti oggetti diversi gestire i comandi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> può essere implementata da un numero qualsiasi di oggetti; questi comprendono controlli Microsoft ActiveX, le implementazioni di visualizzazione finestra, gli oggetti di documenti, le gerarchie di progetto, e agli oggetti VSPackage se stessi (per i comandi globali). In alcuni casi speciali, ad esempio, routing dei comandi in una gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia deve essere implementata.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|DESCRIZIONE|  
|-----------|-----------------|  
|[Implementazione](../../extensibility/internals/command-implementation.md)|Viene descritto come implementare i comandi in un pacchetto VSPackage.|  
|[Disponibilità](../../extensibility/internals/command-availability.md)|Descrive come contesto di Visual Studio determina quali comandi sono disponibili.|  
|[Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md)|Descrive come architettura di routing di comandi di Visual Studio consente i comandi gestire i pacchetti VSPackage diversi.|  
|[Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)|Suggerisce come posizionare i comandi nell'ambiente di Visual Studio.|  
|[Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Viene descritto come i VSPackage possono utilizzare al meglio l'architettura di comandi di Visual Studio.|  
|[Posizionamento predefinito di comandi, gruppi e barre degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Viene descritto come i VSPackage possono meglio usare i comandi inclusi in Visual Studio.|  
|[Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)|Descrive la modalità di caricamento pacchetti VSPackage in Visual Studio.|  
|[File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Vengono fornite informazioni sui file con estensione vsct basato su XML, che vengono usati per descrivere il layout e l'aspetto dei comandi nei pacchetti VSPackage.|
