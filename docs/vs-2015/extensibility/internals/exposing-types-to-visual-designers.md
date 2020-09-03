---
title: Esposizione di tipi alle finestre di progettazione visiva | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691198"
---
# <a name="exposing-types-to-visual-designers"></a>Esposizione di tipi nelle finestre di progettazione visiva
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per visualizzare una finestra di progettazione visiva, è necessario avere accesso alle definizioni di classe e di tipo in fase di progettazione. Le classi vengono caricate da un set predefinito di assembly che includono il set di dipendenze completo del progetto corrente (riferimenti più le relative dipendenze). Potrebbe inoltre essere necessario per le finestre di progettazione visiva accedere alle classi e ai tipi definiti nei file generati dagli strumenti personalizzati.  
  
 I [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemi di progetto e offrono il supporto per l'accesso alle classi e ai tipi generati tramite file eseguibili portatili temporanei (PES temporaneo). Tutti i file generati da uno strumento personalizzato possono essere compilati in un assembly temporaneo, in modo che i tipi vengano caricati da tali assembly ed esposti ai progettisti. L'output di ogni strumento personalizzato viene compilato in un PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo dal fatto che il file generato possa essere compilato o meno. Anche se un progetto non può essere compilato nel suo complesso, i singoli PEs temporanei possono essere ancora disponibili per le finestre di progettazione.  
  
 Il sistema del progetto fornisce supporto completo per il rilevamento delle modifiche apportate al file di output di uno strumento personalizzato, purché queste modifiche siano il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo PE temporaneo e le notifiche appropriate vengono inviate alle finestre di progettazione.  
  
> [!NOTE]
> Poiché il file di generazione eseguibile del programma temporaneo viene eseguito in background, nessun errore viene segnalato all'utente se la compilazione non riesce.  
  
 Gli strumenti personalizzati che sfruttano i vantaggi del supporto PE temporaneo devono rispettare le regole seguenti:  
  
- `GeneratesDesignTimeSource` deve essere impostato su 1 nel registro di sistema.  
  
     Nessun file eseguibile di programma viene compilata senza questa impostazione.  
  
- Il codice generato deve essere nella stessa lingua dell'impostazione del progetto globale.  
  
     Il PE temporaneo viene compilato indipendentemente da ciò che viene segnalato dallo strumento personalizzato come estensione richiesta in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> fornito, che `GeneratesDesignTimeSource` è impostato su 1 nel registro di sistema. Non è necessario che l'estensione sia. vb,. cs o. jsl; può essere qualsiasi estensione.  
  
- Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato autonomamente utilizzando solo il set di riferimenti presenti nel progetto al termine dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> esecuzione.  
  
     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Uno strumento personalizzato che usa un file PE temporaneo deve pertanto generare file di output che possono essere compilati indipendentemente da altri file nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione all'oggetto BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)
