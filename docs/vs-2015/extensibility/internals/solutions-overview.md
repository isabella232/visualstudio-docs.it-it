---
title: Panoramica delle soluzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb3bb85ab172404262c147cce285cebaf756afc9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432072"
---
# <a name="solutions-overview"></a>Panoramica delle soluzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una soluzione è un raggruppamento di uno o più progetti che funzionano insieme per creare un'applicazione. Le informazioni di progetto e lo stato relativi alla soluzione vengono archiviati in due file di soluzione diversa. Il file di soluzione (sln) è basata su testo e possono essere sottoposti a controllo del codice sorgente e condivisi dagli utenti. Il file (con estensione suo) opzione utente della soluzione è binario. Di conseguenza, il file con estensione suo non può essere inserito nel controllo del codice sorgente e contiene informazioni specifiche dell'utente.  
  
 Qualsiasi pacchetto VSPackage può scrivere in entrambi i tipi di file della soluzione. A causa della natura dei file, esistono due diverse interfacce implementate per scrivere su di esse. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia scrive le informazioni di testo nel file con estensione sln e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia scrive il file con estensione suo flussi binari.  
  
> [!NOTE]
> Un progetto non è necessario scrivere in modo esplicito una voce per se stessa nel file di soluzione; l'ambiente di questo problema viene gestito per il progetto. Pertanto, a meno che non si desidera aggiungere altro contenuto in modo specifico per il file della soluzione, è necessario registrare il VSPackage in questo modo.  
  
 Ogni pacchetto VSPackage che supporta la persistenza di soluzione Usa tre interfacce, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia, che viene implementata dall'ambiente e chiamato dal pacchetto VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, che sono entrambi implementati dal pacchetto VSPackage. Il `IVsPersistSolutionOpts` interfaccia deve solo essere implementato se deve essere scritta dal pacchetto VSPackage nel file con estensione suo informazioni private.  
  
 Quando viene aperta una soluzione, il processo seguente viene eseguita.  
  
1. L'ambiente legge la soluzione.  
  
2. Se l'ambiente rileva un `CLSID`, carica il pacchetto VSPackage corrispondente.  
  
3. Se un pacchetto VSPackage viene caricato, l'ambiente chiama `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaccia, per l'interfaccia che richiede il pacchetto VSPackage.  
  
   1. Durante la lettura da un file con estensione sln, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionProps`.  
  
   2. Durante la lettura da un file con estensione suo, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionOpts`.  
  
   Informazioni specifiche relative all'utilizzo di questi file sono reperibile [soluzione (. File sln)](../../extensibility/internals/solution-dot-sln-file.md) e [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
> Se si desidera creare una nuova configurazione soluzione costituito da configurazioni due progetti ed esclusione di un terzo della compilazione, è necessario usare l'interfaccia utente di pagine di proprietà o l'automazione. Non è possibile modificare le configurazioni di gestione di compilazione di soluzioni e le relative proprietà direttamente, ma è possibile modificare il gestore di compilazione della soluzione usando il `SolutionBuild` classe nel modello di automazione DTE. Per altre informazioni sulla configurazione di soluzioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
