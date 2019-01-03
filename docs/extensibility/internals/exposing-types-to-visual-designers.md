---
title: Esposizione di tipi di finestre di progettazione visiva | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 713b44c9ccf360af04086b32c121f7e26c0e67d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859370"
---
# <a name="expose-types-to-visual-designers"></a>Esporre i tipi di finestre di progettazione visiva
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve avere accesso alle definizioni di classe e il tipo in fase di progettazione per visualizzare una finestra di progettazione. Le classi vengono caricate da un set predefinito di assembly che includono il set completo delle dipendenze del progetto corrente (riferimenti e le relative dipendenze). Potrebbe essere necessario anche per finestre di progettazione visiva per accedere alle classi e tipi definiti nei file generati da strumenti personalizzati.  
  
 Il [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemi di progetto forniscono il supporto per l'accesso alle classi generate e i tipi tramite portatile temporaneo file eseguibili (file PE temporanei). Qualsiasi file generati da uno strumento personalizzato può essere compilato in un assembly temporaneo in modo che i tipi possono essere caricati da tali assembly ed esposte nelle finestre di progettazione. L'output di ogni strumento personalizzato viene compilato in un file PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo se il file generato può essere compilato. Anche se un progetto non venga compilato nel suo complesso, i singoli file PE temporaneo potrebbero essere ancora disponibili nelle finestre di progettazione.  
  
 Il sistema di progetto fornisce supporto completo per tenere traccia delle modifiche al file di output di uno strumento personalizzato, purché queste modifiche sono il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo file PE temporaneo, e le notifiche appropriate vengono inviate alle finestre di progettazione.  
  
> [!NOTE]
>  Perché file di generazione eseguibile di programma temporaneo avviene in background, non vengono segnalati errori all'utente se la compilazione ha esito negativo.  
  
 Gli strumenti personalizzati che sfruttano i vantaggi del supporto PE temporaneo devono rispettare le regole seguenti:  
  
-   **GeneratesDesignTimeSource** deve essere impostata su 1 nel Registro di sistema.  
  
     Nessuna compilazione file eseguibile di programma viene eseguito senza questa impostazione.  
  
-   Il codice generato deve essere nella stessa lingua come l'impostazione di progetti globale.  
  
     Indipendentemente dal report che lo strumento personalizzato come l'estensione nella richiesta viene compilato il file PE temporaneo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> purché **GeneratesDesignTimeSource** è impostato su 1 nel Registro di sistema. L'estensione non deve essere *vb*, *cs*, o *JLS*; può essere qualsiasi estensione.  
  
-   Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato in proprio utilizzando solo il set di riferimenti presenti nel progetto al momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termina l'esecuzione.  
  
     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Pertanto, uno strumento personalizzato che usa un file PE temporaneo necessario generare i file di output che possono essere compilati indipendentemente da altri file nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione all'oggetto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementare generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)   
 [Registrare i generatori di file singolo](../../extensibility/internals/registering-single-file-generators.md)