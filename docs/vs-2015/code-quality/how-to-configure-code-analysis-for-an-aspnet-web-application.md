---
title: "Procedura: Configura analisi codice per un'applicazione Web ASP.NET | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8e75f5a584dd0522240f8b4d45cb28107bca38e3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113410"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Procedura: Configurare l'analisi codice per un'applicazione Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelle [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] è possibile selezionare da un elenco di analisi del codice *set di regole* da applicare a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione Web. Il set di regole predefinito è regole minime consigliate di Microsoft. È possibile selezionare un'altra regola da applicare al sito Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Per configurare un set di regole per un progetto del framework di pagine ASP.NET  
  
1. Selezionare il sito Web in **Esplora soluzioni**.  
  
2. Nel **Analyze** menu, fare clic su **Configura analisi codice per sito Web**.  
  
3. Se è stata selezionata la soluzione e la soluzione contiene più di un progetto, selezionare il sistema operativo di configurazione e di destinazione compilazione dal **Configuration** e **piattaforma** Elenca.  
  
4. Per ogni progetto nella soluzione, scegliere il **del Set di regole** colonna e quindi scegliere il nome della regola impostata per l'esecuzione.  
  
5. Per impostazione predefinita, l'analisi del codice viene eseguito su tutti i progetti nella soluzione. Per disabilitare o abilitare l'analisi codice per un particolare progetto, seguire questa procedura:  
  
    1. Il pulsante destro del mouse e quindi fare clic su proprietà.  
  
    2. Selezionare o deselezionare i **Attiva analisi codice** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice selezionando **Esegui analisi del codice sul sito Web** dalle **Analizza** menu.  
  
6. Nel **eseguire questo set di regole** elenco a discesa elenco, seguire questa procedura:  
  
    - Selezionare il set di regole che si desidera utilizzare.  
  
    - Selezionare  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non incluso nell'elenco.  
  
    - Definire un set di regole personalizzato. Per altre informazioni, vedere [creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).
