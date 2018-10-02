---
title: "Procedura: configurare l'analisi codice per un'applicazione Web ASP.NET | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b611e303c61e7be9586d6d746e5c859c8dbb5b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526197"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: Configura analisi codice per un'applicazione Web ASP.NET](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application).  
  
Nelle [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] è possibile selezionare da un elenco di analisi del codice *set di regole* da applicare a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione Web. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile selezionare un'altra regola da applicare al sito Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Per configurare un set di regole per un progetto del framework di pagine ASP.NET  
  
1.  Selezionare il sito Web in **Esplora soluzioni**.  
  
2.  Nel **Analyze** menu, fare clic su **Configura analisi codice per sito Web**.  
  
3.  Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare il sistema operativo di configurazione e di destinazione compilazione dal **Configuration** e **piattaforma** Elenca.  
  
4.  Per ogni progetto nella soluzione, scegliere il **del Set di regole** colonna e quindi scegliere il nome della regola impostata per l'esecuzione.  
  
5.  Per impostazione predefinita, l'analisi del codice viene eseguito su tutti i progetti nella soluzione. Per disabilitare o abilitare l'analisi codice per un particolare progetto, seguire questa procedura:  
  
    1.  Il pulsante destro del mouse e quindi fare clic su proprietà.  
  
    2.  Selezionare o deselezionare i **Attiva analisi codice** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi del codice sul sito Web** dalle **Analizza** menu.  
  
6.  Nel **eseguire questo set di regole** elenco a discesa elenco, seguire questa procedura:  
  
    -   Selezionare il set di regole che si desidera utilizzare.  
  
    -   Selezionare  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non incluso nell'elenco.  
  
    -   Definire un set di regole personalizzato. Per altre informazioni, vedere [creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).



