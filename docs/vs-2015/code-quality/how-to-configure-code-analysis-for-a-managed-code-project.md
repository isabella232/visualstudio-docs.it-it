---
title: "Procedura: configurare l'analisi codice per un progetto di codice gestito | Microsoft Docs"
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
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 34c3088aee4089c69669eaa3af5a08a657553363
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540431"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procedura: Configurare l'analisi codice per un progetto di codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: Configura analisi codice per un progetto di codice gestito](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-a-managed-code-project).  
  
Nelle [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] e [!INCLUDE[vsPro](../includes/vspro-md.md)], è possibile scegliere da un elenco di analisi del codice *set di regole* da applicare a un progetto di codice gestito. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile applicare un altro set di regole a un progetto o a tutti i progetti in una soluzione.  
  
> [!NOTE]
>  Per informazioni su come configurare una set di regole per le applicazioni Web ASP.NET, vedere [procedura: Configura analisi codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Per configurare una set di regole per un progetto .NET Framework  
  
1.  Nelle **Esplora soluzioni**, fare clic con il progetto.  
  
2.  Nel **Analyze** menu, fare clic su **Configura analisi codice per** *NomeProgetto*.  
  
3.  Nel **Configuration** e **piattaforma** elenchi, scegliere la piattaforma di destinazione e configurazione di compilazione.  
  
4.  Per eseguire l'analisi del codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare la **Abilita analisi codice su compilazione (definisce la costante CODE_ANALYSIS)** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice aprendo il **Analyze** menu e scegliendo **Esegui analisi del codice** *NomeProgetto*.  
  
5.  Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi del codice generato, deselezionare il **non visualizzare i risultati dal codice generato** casella di controllo.  
  
    > [!NOTE]
    >  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
6.  Nel **eseguire questo set di regole** elenco, effettuare una delle operazioni seguenti:  
  
    -   Fare clic sul set di regole che si desidera utilizzare.  
  
    -   Fare clic su  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non incluso nell'elenco.  
  
    -   Definire un set di regole personalizzato.  
  
         Per altre informazioni, vedere [creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: configurazione e uso di un set di regole personalizzate](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)



