---
title: Esposizione di tipi di finestre di progettazione visiva | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e09161d7ea2e27fbc1f4c7bd68cc7da952d3f1d9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525911"
---
# <a name="exposing-types-to-visual-designers"></a>Esposizione di tipi nelle finestre di progettazione visiva
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [che espone i tipi di finestre di progettazione visiva](https://docs.microsoft.com/visualstudio/extensibility/internals/exposing-types-to-visual-designers).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] deve avere accesso alle definizioni di classe e il tipo in fase di progettazione per visualizzare una finestra di progettazione. Le classi vengono caricate da un set predefinito di assembly che includono il set completo delle dipendenze del progetto corrente (riferimenti e le relative dipendenze). Potrebbe essere necessario anche per finestre di progettazione visiva per accedere alle classi e tipi definiti nei file generati da strumenti personalizzati.  
  
 Il [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemi di progetto forniscono il supporto per l'accesso alle classi generate e i tipi tramite portatile temporaneo file eseguibili (file PE temporanei). Qualsiasi file generati da uno strumento personalizzato può essere compilato in un assembly temporaneo in modo che i tipi possono essere caricati da tali assembly ed esposte nelle finestre di progettazione. L'output di ogni strumento personalizzato viene compilato in un file PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo se il file generato può essere compilato. Anche se un progetto non venga compilato nel suo complesso, singoli file PE temporaneo potrebbe essere ancora disponibili nelle finestre di progettazione.  
  
 Il sistema di progetto fornisce supporto completo per tenere traccia delle modifiche al file di output di uno strumento personalizzato, purché queste modifiche sono il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo file PE temporaneo, e le notifiche appropriate vengono inviate alle finestre di progettazione.  
  
> [!NOTE]
>  Perché file di generazione eseguibile di programma temporaneo avviene in background, non vengono segnalati errori all'utente se la compilazione ha esito negativo.  
  
 Gli strumenti personalizzati che sfruttano i vantaggi del supporto PE temporaneo devono rispettare le regole seguenti:  
  
-   `GeneratesDesignTimeSource` deve essere impostato su 1 nel Registro di sistema.  
  
     Nessuna compilazione file eseguibile di programma viene eseguito senza questa impostazione.  
  
-   Il codice generato deve essere nella stessa lingua come l'impostazione di progetti globale.  
  
     Indipendentemente dal report che lo strumento personalizzato come l'estensione nella richiesta viene compilato il file PE temporaneo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> purché `GeneratesDesignTimeSource` è impostato su 1 nel Registro di sistema. L'estensione non dovrà essere JLS; con estensione cs o vb può essere qualsiasi estensione.  
  
-   Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato in proprio utilizzando solo il set di riferimenti presenti nel progetto al momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termina l'esecuzione.  
  
     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Pertanto, uno strumento personalizzato che usa un file PE temporaneo necessario generare i file di output che possono essere compilati indipendentemente da altri file nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione all'oggetto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementazione di generatori di File singoli](../../extensibility/internals/implementing-single-file-generators.md)   
 [Stabilire il Namespace predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)

