---
title: Panoramica del multitargeting di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6fcc7f1a1fb7b9f348ace817c800a5e353694e96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531128"
---
# <a name="visual-studio-multi-targeting-overview"></a>Cenni preliminari sul multitargeting di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Visual Studio Cenni preliminari sul multitargeting](https://docs.microsoft.com/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
In questa versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile specificare la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] necessaria per l'applicazione. Pertanto, se si intende usare questa versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per continuare a sviluppare un progetto che è stato avviato in una versione precedente, non è necessario modificare la destinazione del framework. È anche possibile creare una soluzione contenente progetti destinati a versioni diverse del framework. La definizione della destinazione del framework consente anche di garantire che l'applicazione usi solo le funzionalità disponibili nella versione specificata del framework.  
  
> [!TIP]
>  È anche possibile definire la destinazione delle applicazioni per piattaforme diverse. Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)  
  
## <a name="framework-targeting-features"></a>Funzionalità di definizione della destinazione del framework  
 La definizione della destinazione del framework include le seguenti funzionalità:  
  
-   Quando si apre un progetto destinato a una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], con [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] è possibile aggiornarla automaticamente o lasciare invariata la destinazione.  
  
-   Quando si crea un progetto, è possibile specificare la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che si vuole usare come destinazione.  
  
-   È possibile modificare la versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a cui è destinato un progetto esistente.  
  
-   È possibile definire la destinazione di una versione diversa del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in ognuno dei numerosi progetti nella stessa soluzione.  
  
-   Quando si modifica la versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a cui è destinato un progetto, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] effettua tutte le modifiche necessarie ai riferimenti e ai file di configurazione.  
  
 Quando si lavora su un progetto destinato a una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio modifica in modo dinamico l'ambiente di sviluppo, come indicato di seguito:  
  
-   Vengono filtrati gli elementi delle finestre di dialogo **Nuovo progetto**, **Aggiungi nuovo elemento**, **Aggiungi nuovo riferimento** **Aggiungi riferimento al servizio** per omettere scelte che non sono disponibili nella versione di destinazione.  
  
-   Vengono filtrati i controlli personalizzati nella **Casella degli strumenti** per rimuovere quelli che non sono disponibili nella versione di destinazione e per visualizzare solo i controlli più aggiornati quando sono disponibili più controlli.  
  
-   Vengono applicati i filtri IntelliSense per omettere funzionalità del linguaggio che non sono disponibili nella versione di destinazione.  
  
-   Vengono filtrate le proprietà nella finestra **Proprietà** per omettere quelle che non sono disponibili nella versione di destinazione.  
  
-   Vengono filtrate le opzioni di menu per omettere opzioni che non sono disponibili nella versione di destinazione.  
  
-   Per le compilazioni, vengono usate la versione e le opzioni del compilatore appropriate per la versione di destinazione.  
  
> [!NOTE]
>  La definizione della destinazione del framework non garantisce che l'applicazione verrà eseguita correttamente. È necessario testare l'applicazione per assicurarsi che venga eseguita la versione di destinazione. Non è possibile usare come destinazione versioni di framework precedenti a .NET Framework 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Selezione di una versione del framework di destinazione  
 Quando si crea un progetto, selezionare la versione [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] di destinazione nella finestra di dialogo **Nuovo progetto**. L'elenco dei modelli di progetto disponibili viene filtrato in base alla selezione. In un progetto esistente, è possibile modificare la versione [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] di destinazione nella finestra di dialogo delle proprietà del progetto. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  Nelle edizioni Express di Visual Studio, non è possibile impostare il framework di destinazione nella finestra di dialogo **Nuovo progetto**.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Risoluzione dei riferimenti ad assembly di sistema e utente  
 Per impostare come destinazione una versione di .NET Framework, è necessario prima installare i riferimenti dell'assembly appropriato. I riferimenti degli assembly per .NET Framework versioni 2.0, 3.0 e 3.5 sono inclusi in .NET Framework 3.5 SP1, scaricabile dal sito Web [Area download Microsoft, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602). I riferimenti degli assembly per .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile e Silverlight sono disponibili anche nei siti Web relativi ai [download di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Un profilo client di .NET Framework è un sottoinsieme di .NET Framework che offre un set limitato di librerie e funzionalità. Per altre informazioni sui profili di client, vedere [Profilo client .NET Framework](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
 La finestra di dialogo **Aggiungi riferimento** disabilita gli assembly di sistema non pertinenti alla versione di destinazione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in modo che non possano essere aggiunti a un progetto inavvertitamente. (Gli assembly di sistema sono file con estensione dll inclusi in una versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].) I riferimenti che appartengono a una versione del framework successiva alla versione di destinazione non verranno risolti e i controlli che dipendono da un riferimento di questo tipo non possono essere aggiunti. Se si vuole abilitare questo riferimento, reimpostare la destinazione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] del progetto su una in cui sia incluso il riferimento.  Per altre informazioni, vedere [Introduzione a Creazione progetti](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
 Per altre informazioni sui riferimenti ad assembly, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Attivazione di LINQ  
 Quando si definisce la destinazione di .NET Framework 3.5 o versioni successive, vengono aggiunti automaticamente un riferimento a System.Core e un'importazione a livello di progetto per System.Linq (solo in Visual Basic). Per usare le funzionalità LINQ, è necessario attivare anche Option Infer (solo in Visual Basic). Se si passa a una versione precedente di .NET Framework, il riferimento e l'importazione vengono rimossi automaticamente. Per altre informazioni, vedere [Procedura: Creare un progetto LINQ](http://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).  
  
## <a name="see-also"></a>Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [.NET Framework Multi-Targeting for ASP.NET Web Projects](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)  (Multitargeting .NET Framework per progetti Web ASP.NET)  
 [Platform compatibility and system requirements](http://www.microsoft.com/visualstudio/eng/products/compatibility) (Requisiti di sistema e compatibilità delle piattaforme)



